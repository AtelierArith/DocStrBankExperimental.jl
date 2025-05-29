```
RMSEVariable(short_name, model_names::Vector{String})
```

`short_name`の変数と`model_names`のモデル名を持つRMSEVariableを構築します。

カテゴリはデフォルトで「ANN」、「DJF」、「MAM」、「JJA」、「SON」です。二乗平均平方根誤差はデフォルトで`NaN`です。各モデルの単位は空文字列で示されるため、欠落しています。
