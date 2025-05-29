```
error_if_direct_mode(model::Model, func::Symbol)
```

`model`が`func`という名前の関数からの呼び出し中に直接モードにある場合にエラーを発生させます。

JuMP内で内部的に使用されるか、直接モードのモデルをサポートしたくないJuMP拡張によって使用されます。
