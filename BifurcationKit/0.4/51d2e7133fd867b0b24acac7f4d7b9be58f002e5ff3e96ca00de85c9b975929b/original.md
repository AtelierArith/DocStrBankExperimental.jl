```julia
struct DefaultLS <: BifurcationKit.AbstractDirectLinearSolver
```

This struct is used to provide the backslash operator ``. Can be used to solve`(a₀ * I + a₁ * J) * x = rhs`.

## Fields

  * `useFactorization::Bool`: Whether to catch a factorization for multiple solves. Some operators may not support LU (like ApproxFun.jl) or QR factorization so it is best to let the user decides. Some matrices do not have `factorize` like `StaticArrays.MMatrix`. Default: true
