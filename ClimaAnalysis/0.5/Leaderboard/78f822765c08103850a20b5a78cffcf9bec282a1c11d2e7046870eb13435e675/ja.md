```
RMSEVariable(short_name,
             model_names::Vector{String},
             category_names::Vector{String},
             units::Dict)
```

`short_name`の変数名、`model_names`のモデル名、`category_names`のカテゴリ、そしてモデル名から単位へのマッピングを持つ辞書`units`に提供された単位を使用してRMSEVariableを構築します。

二乗平均平方根誤差はデフォルトで`NaN`になります。辞書`units`に欠けているモデルは、空の文字列で示される欠損単位を持ちます。
