```
RMSEVariable(short_name, model_names::Vector{String}, units::String)
```

`short_name`の変数名、`model_names`にあるモデルの名前、および各モデル名を`units`にマッピングする単位を指定してRMSEVariableを構築します。

カテゴリはデフォルトで「ANN」、「DJF」、「MAM」、「JJA」、「SON」です。二乗平均平方根誤差はデフォルトで`NaN`です。

これは、すべてのモデルが同じ単位を共有する場合に便利です。
