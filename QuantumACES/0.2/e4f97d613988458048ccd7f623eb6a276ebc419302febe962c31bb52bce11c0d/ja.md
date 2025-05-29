```
get_transform(d::Design, est_type::Symbol)
```

ゲートの固有値を、推定器のタイプ `est_type`（`:ordinary`、`:marginal`、または `:relative`）に依存するゲートの固有値にマッピングする変換行列を返します。これは、設計 `d` のゲートデータを使用して計算されます。
