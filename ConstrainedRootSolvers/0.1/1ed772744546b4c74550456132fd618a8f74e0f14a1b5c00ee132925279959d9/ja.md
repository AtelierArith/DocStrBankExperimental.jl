2Dおよびそれ以上の解に対する許容範囲

```julia
struct SolutionToleranceND{FT} <: ConstrainedRootSolvers.AbstractTolerance{FT}
```

# フィールド

  * `tol::Vector`: 解に対する許容範囲
  * `n_limit::Int64`: イテレーションの制限
