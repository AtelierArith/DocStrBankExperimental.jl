```
ContinuousTimeHab{C <: Number, M <: AbstractArray{C, 3}} <: AbstractHabitat{C}
```

このハビタットのサブタイプは、任意の単位のハビタット行列 `matrix`、現在操作中のハビタット行列の時間スライス `time`、グリッドスクエアのサイズ `size`、およびハビタット更新タイプ `change` を保持します。
