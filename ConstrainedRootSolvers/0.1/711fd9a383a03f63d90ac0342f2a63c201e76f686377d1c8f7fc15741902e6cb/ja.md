ターゲット関数残差の許容値

```julia
struct ResidualTolerance{FT} <: ConstrainedRootSolvers.AbstractTolerance{FT}
```

# フィールド

  * `tol::Any`: 残差の許容値
  * `n_limit::Int64`: イテレーションの制限
