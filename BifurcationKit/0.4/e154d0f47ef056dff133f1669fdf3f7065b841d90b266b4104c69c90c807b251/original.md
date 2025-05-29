```julia
struct LSFromBLS{Ts} <: BifurcationKit.AbstractLinearSolver
```

This structure is used to provide the following linear solver. To solve (1) J⋅x = rhs, one decomposes J using Matrix by blocks and then use a bordering strategy to solve (1).

> It is interesting for solving the linear system associated with Collocation / Trapezoid functionals, for example using `BorderingBLS(solver = BK.LSFromBLS(), tol = 1e-9, k = 2, check_precision = true)`


  * `solver::Any`: Linear solver used to solve the smaller linear systems.

!!! warn "Warning"
    The solver only works for `AbstractMatrix`

