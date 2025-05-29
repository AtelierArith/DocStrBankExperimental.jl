```
hclt(data, num_hidden_cats; num_cats = nothing, input_type = LiteralDist)
```

データからHiddenChowLiuTree (hclt) 回路構造を学習します。

  * `data`: 行列またはCuMatrix
  * `num_hidden_cats`: 隠れ変数のカテゴリ数
  * `input_type`: 入力の分布タイプ
  * `num_cats`: カテゴリカル入力の場合のカテゴリ数。明示的に指定されていない場合は自動的に推定されます。
