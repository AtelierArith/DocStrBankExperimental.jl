```
constraint_supports(optimizer_model::JuMP.Model, 
                    cref::InfOptConstraintRef,
                    key::Val{ext_key_name}; [kwargs...])
```

`optimizer_model`内の`cref`のマッピングに関連付けられたサポートを返します。これは`key`に基づいてディスパッチされ、オプティマイザーモデルの拡張を許可します。`cref`が`optimizer_model`に保存されている変数マッピングに関連付けられていない場合は、エラーをスローする必要があります。必要に応じてキーワード引数を追加できます。
