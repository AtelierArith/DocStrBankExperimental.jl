```
variable_supports(optimizer_model::JuMP.Model, vref,
                  key::Val{ext_key_name}; 
                  [kwargs...])::Vector
```

`optimizer_model`内の`vref`のマッピングに関連付けられたサポートを返します。これは`key`に基づいてディスパッチされ、オプティマイザーモデルの拡張を許可します。`vref`が`optimizer_model`に保存されている変数マッピングに関連付けられていない場合はエラーが発生します。必要に応じてキーワード引数を追加できます。ポイントまたは有限変数には拡張は必要ないことに注意してください。
