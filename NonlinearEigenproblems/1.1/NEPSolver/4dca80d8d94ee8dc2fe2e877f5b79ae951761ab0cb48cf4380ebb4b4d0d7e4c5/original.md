```
struct IARInnerSolver
function IARInnerSolver(;tol=1e-13,maxit=80,
           starting_vector=:ones,normalize_DEPs=:auto,
           iar_function=iar)
```

Uses [`iar`](@ref), [`tiar`](@ref) or [`iar_chebyshev`](@ref) to solve the inner problem, with tolerance, and maximum number of iterations given by `tol` and `maxit`. The starting vector can be `:ones` or `:randn`. The `iar_function` can be `iar`, `tiar` or `iar_chebyshev` (or any function taking the same parameters as input). `normalize_DEPs` determines if the we should carry out precomputation and make sure the projection of a [`DEP`](@ref)  is again a `DEP` (which can speed up performance). It can take the value `true`, `false` or `:auto`. `:auto` sets it to true if we use the `iar_chebyshev` solver.

The kwarg `iar_function`, specifies a `Function` which is called. Examples of functions are `iar` and `iar_chebyshev`. It can be any NEP-solver which takes the same keyword arguments as these methods.

See also: [`InnerSolver`](@ref), [`inner_solve`](@ref)
