```
RMSEVariable(short_name::String,
             model_names::Vector{String},
             category_names::Vector{String},
             RMSEs,
             units::String)
```

`short_name`の変数名、`model_names`のモデル名、`category_names`のカテゴリ、`RMSEs`の平方根平均二乗誤差、および各モデル名を`units`にマッピングする単位を持つRMSEVariableを構築します。

これは、すべてのモデルが同じ単位を共有する場合に便利です。
