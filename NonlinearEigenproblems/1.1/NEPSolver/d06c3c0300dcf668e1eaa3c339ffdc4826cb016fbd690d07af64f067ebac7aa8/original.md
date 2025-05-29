```
struct NleigsInnerSolver <: InnerSolver
function NleigsInnerSolver(;Σ= :auto,nodes =:auto, tol=1e-6 )
```

Uses [`nleigs`](@ref) to solve the inner problem, in the region `Σ` with shifts `nodes` and with tolerance `tol`. If the variable `Σ` is set to `:auto`, the region `Σ` will be set by using the eigenvalues approximations. See [`nleigs`](@ref) for description of parameters.

See also: [`InnerSolver`](@ref), [`inner_solve`](@ref)
