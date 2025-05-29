```
sol = find_zero(
        f::F,
        method::RootSolvingMethod{FT},
        soltype::SolutionType,
        tol::Union{Nothing, AbstractTolerance} = nothing,
        maxiters::Int = 10_000,
        )
```

Finds the nearest root of `f`. Returns a the value of the root `x` such that `f(x) ≈ 0`, and a Boolean value `converged` indicating convergence.

  * `f` function of the equation to find the root
  * `method` can be one of:

      * `SecantMethod()`: [Secant method](https://en.wikipedia.org/wiki/Secant_method)
      * `RegulaFalsiMethod()`: [Regula Falsi method](https://en.wikipedia.org/wiki/False_position_method#The_regula_falsi_(false_position)_method)
      * `NewtonsMethodAD()`: [Newton's method](https://en.wikipedia.org/wiki/Newton%27s_method) using Automatic Differentiation
      * `NewtonsMethod()`: [Newton's method](https://en.wikipedia.org/wiki/Newton%27s_method)
  * `soltype` is a solution type which may be one of:    `CompactSolution` GPU-capable. Solution has `converged` and `root` only, see [`CompactSolutionResults`](@ref)    `VerboseSolution` CPU-only. Solution has additional diagnostics, see [`VerboseSolutionResults`](@ref)
  * `tol` is a tolerance type to determine when to stop iterations.
  * `maxiters` is the maximum number of iterations.
