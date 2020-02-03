## How to use your own field method from the ActiveForm instance

### 1) Example:
```
<?= $form->field($model, 'is_active')->switch() ?>
```

### 2) Let's configure Dependecy Injection Definition (using DI Container):
```
\Yii::$container->set('yii\bootstrap4\ActiveForm', ['fieldClass' => 'admin\ui\ActiveField']);
```
### 3) Your own ActiveField:
```
<?php
namespace frontend\components\ui;

class ActiveField extends \yii\widgets\ActiveField
{
    /**
     * @param array $options
     * @return \yii\widgets\ActiveField
     */
    public function switch($options = [])
    {
        $this->checkTemplate = "<div class=\"custom-control custom-switch custom-checkbox\">\n{input}\n{label}\n{error}\n{hint}\n</div>";
        return parent::checkbox($options);
    }
}
```
