解の許容範囲

```julia
struct SolutionTolerance{FT} <: ConstrainedRootSolvers.AbstractTolerance{FT}
```

# フィールド

  * `tol::Any`: 解の許容範囲
  * `n_limit::Int64`: イテレーションの制限
