```
extend_vpolytope_by_densitystates(
    sepPolytope::VPolytope{Float64,Array{Float64,1}},
    sepDensityStates::Array{DensityState},
    precision::Integer
)
```

与えられた多面体 `sepPolytope` と新しい分離可能な `sepDensityStates` を新しい頂点として基にした分離可能状態の多面体の拡張された Lazysets.VPolytope 表現を返します。
