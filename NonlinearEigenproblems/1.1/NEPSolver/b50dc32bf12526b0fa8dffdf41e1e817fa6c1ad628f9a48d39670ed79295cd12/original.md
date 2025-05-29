```
struct ContourBeynInnerSolver <: InnerSolver
function ContourBeynInnerSolver(;tol=sqrt(eps(real(Float64))),
                                radius=:auto,N=1000)
```

Uses [`contour_beyn`](@ref) to solve the inner problem, with radius and number of quadrature nodes, given by `radius` and `n`. If the variable `radius` is set to `:auto`, the integration radius will be automatically selected by using the eigenvalue approximations specified by the outer solver.

See also: [`InnerSolver`](@ref), [`inner_solve`](@ref)
