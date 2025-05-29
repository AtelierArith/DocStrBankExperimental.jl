```
struct NewtonInnerSolver
function NewtonInnerSolver(;tol=1e-13,maxit=80,starting_vector=:Vk,
                           newton_function=augnewton)
```

Uses a Newton-like method to solve the inner problem, with tolerance, and maximum number of iterations given by `tol` and `maxit`. The starting vector can be `:ones`, `:randn`, or `:Vk`. The value `:Vk` specifies the use of the outer NEP-solver keyword argument (`Vk`). This is typically the previous iterate in the outer method.

The kwarg `newton_function`, specifies a `Function` which is called. The type supports [`augnewton`](@ref), [`newton`](@ref), [`resinv`](@ref) [`quasinewton`](@ref), [`newtonqr`](@ref). In principle it can be any method which takes the same keyword arguments as these methods.

See also: [`InnerSolver`](@ref), [`inner_solve`](@ref)
