```
project(M::GeneralizedStiefel, p)
```

埋め込みから[`GeneralizedStiefel`](@ref) `M`へのプロジェクト`p`、すなわち、$p$の極分解として`q`を計算し、$q^{\mathrm{H}}Bq$が単位行列となるようにします。ここで、$⋅^{\mathrm{H}}$はエルミート、すなわち複素共役転置を示します。
