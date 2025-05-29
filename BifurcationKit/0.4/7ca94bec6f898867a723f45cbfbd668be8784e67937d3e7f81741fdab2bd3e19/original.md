```julia
struct MatrixFreeBLS{S<:Union{Nothing, BifurcationKit.AbstractLinearSolver}} <: BifurcationKit.AbstractBorderedLinearSolver
```

This struct is used to  provide the bordered linear solver based a matrix free operator for the full system in `(x, p)`.

## Constructor

```
MatrixFreeBLS(solver, ::Bool)
```

## Fields

  * `solver::Union{Nothing, BifurcationKit.AbstractLinearSolver}`: Linear solver for solving the extended linear system
  * `use_bordered_array::Bool`: What is the structure used to hold `(x, p)`. If `true`, this is achieved using `BorderedArray`. If `false`, a `Vector` is used.
