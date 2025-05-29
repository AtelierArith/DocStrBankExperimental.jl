```
make_explicit_tendency(model::Soil.RichardsModel)
```

関数 `make_compute_imp_tendency` の拡張で、リチャードソン-リチャーズ方程式用です。

RHS の明示的項の傾向計算関数を構築します。これには、水平成分とソース/シンク項が含まれます。
