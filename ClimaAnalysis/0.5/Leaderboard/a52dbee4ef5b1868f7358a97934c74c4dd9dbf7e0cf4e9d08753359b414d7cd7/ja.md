```
RMSEVariable(short_name,
             model_names::Vector{String},
             category_names::Vector{String},
             units::String)
```

`short_name`の変数名、`model_names`のモデル名、`category_names`のカテゴリ、各モデル名を`units`にマッピングする単位を持つRMSEVariableを構築します。

二乗平均平方根誤差はデフォルトで`NaN`になります。

これは、すべてのモデルが同じ単位を共有する場合に便利です。
