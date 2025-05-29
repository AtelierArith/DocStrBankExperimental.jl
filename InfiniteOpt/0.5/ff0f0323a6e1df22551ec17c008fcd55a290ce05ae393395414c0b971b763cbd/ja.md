```
expression_supports(optimizer_model::JuMP.Model, expr,
                    key::Val{ext_key_name}; [kwargs...])
```

`optimizer_model`内の`expr`のマッピングに関連付けられたサポートを返します。これは`key`に基づいてディスパッチされ、オプティマイザーモデルの拡張を許可します。`expr`が`optimizer_model`に保存されている変数マッピングに関連付けられていない場合、エラーが発生します。必要に応じてキーワード引数を追加できます。`expr`が`GeneralVariableRef`の場合、これは単に`variable_supports`にディスパッチされます。
