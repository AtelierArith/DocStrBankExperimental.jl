```julia
struct VUMPSSvdCut <: MPSKit.Algorithm
```

An algorithm that uses a two-site update step to change the bond dimension of a state.

## Fields

  * `alg_gauge::Any`: algorithm used for gauging the `InfiniteMPS`
  * `alg_eigsolve::Any`: algorithm used for the eigenvalue solvers
  * `alg_svd::Any`: algorithm used for the singular value decomposition
  * `trscheme::TensorKit.TruncationScheme`: algorithm used for [truncation][@extref TensorKit.tsvd] of the two-site update
