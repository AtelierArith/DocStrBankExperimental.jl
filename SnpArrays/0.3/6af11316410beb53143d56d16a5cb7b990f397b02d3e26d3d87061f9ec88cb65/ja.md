```
SnpLinAlg{T}(s; model=ADDITIVE_MODEL, center=false, scale=false, impute=true)
```

線形代数操作のためにいくつかのパラメータで `SnpArray` をパディングします。

# 引数

  * s: `SnpArray`。
  * model: `ADDITIVE_MODEL`（デフォルト）、`DOMINANT_MODEL`、`RECESSIVE_MODEL` のいずれか。
  * center: 中心化するかどうか（デフォルト: false）。
  * scale: 標準偏差1にスケーリングするかどうか（デフォルト: false）。
  * impute: 欠損値を列の平均で補完するかどうか（デフォルト: true）。
