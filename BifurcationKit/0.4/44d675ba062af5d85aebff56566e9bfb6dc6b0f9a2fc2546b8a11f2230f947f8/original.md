```julia
struct MatrixBLS{S<:Union{Nothing, BifurcationKit.AbstractLinearSolver}} <: BifurcationKit.AbstractBorderedLinearSolver
```

This struct is used to  provide the bordered linear solver based on inverting the full matrix.

  * `solver::Union{Nothing, BifurcationKit.AbstractLinearSolver}`: Linear solver used to invert the full matrix.
