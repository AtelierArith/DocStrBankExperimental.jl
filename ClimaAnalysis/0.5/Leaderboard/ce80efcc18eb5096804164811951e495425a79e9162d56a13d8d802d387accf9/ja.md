```
RMSEVariable(short_name, model_names::Vector{String}, units::Dict)
```

`short_name`の変数名、`model_names`にあるモデルの名前、およびモデル名から単位へのマッピングを提供する辞書`units`を使用してRMSEVariableを構築します。

カテゴリはデフォルトで「ANN」、「DJF」、「MAM」、「JJA」、「SON」です。二乗平均平方根誤差はデフォルトで`NaN`です。辞書`units`に欠けているモデルは、空の文字列で示される欠損単位を持ちます。
