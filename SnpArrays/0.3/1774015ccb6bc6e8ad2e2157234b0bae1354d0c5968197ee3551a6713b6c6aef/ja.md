```
SnpBitMatrix{T}(s; model=ADDITIVE_MODEL, center=false, scale=false)
```

`AbstractSnpArray` `s`を2つの`BitMatrix`として保存し、線形代数を簡素化します。

# 引数

  * s: `AbstractSnpArray`。
  * model: `ADDITIVE_MODEL`（デフォルト）、`DOMINANT_MODEL`、`RECESSIVE_MODEL`のいずれか。
  * center: 中心化するかどうか（デフォルト: false）。
  * scale: 標準偏差1にスケールするかどうか（デフォルト: false）。
