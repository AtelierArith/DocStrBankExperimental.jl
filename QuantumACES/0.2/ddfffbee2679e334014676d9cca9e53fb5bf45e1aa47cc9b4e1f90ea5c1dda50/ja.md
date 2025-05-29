```
get_pad_transform(d::Design, est_type::Symbol; probabilities::Bool = false)
```

ゲートの固有値をパディングする変換行列、または `probabilities` が `true` の場合はゲートエラー確率を返します。これらのタイプは、推定器のタイプ `est_type`（`:ordinary`、`:marginal`、または `:relative`）に依存し、設計 `d` のゲートデータを使用して計算された単位固有値またはエラー確率になります。
