```
function IARChebInnerSolver(;tol=1e-13,maxit=80,starting_vector=:ones,
                            normalize_DEPs=true)
```

Uses [`iar_chebyshev`](@ref) to solve the inner problem. See [`IARInnerSolver`](@ref) for keyword argument documentation.

See also: [`IARInnerSolver`](@ref), [`InnerSolver`](@ref), [`inner_solve`](@ref)
