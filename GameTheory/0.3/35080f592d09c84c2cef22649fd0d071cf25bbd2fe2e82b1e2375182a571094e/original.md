```
outerapproximation(rpd; nH=32, tol=1e-8, maxiter=500, check_pure_nash=true,
                   verbose=false, nskipprint=50,
                   plib=CDDLib.Library(),
                   lp_solver=GameTheory.highs_optimizer_silent)
```

Approximates the set of equilibrium values for a repeated game with the outer hyperplane approximation described by Judd, Yeltekin, Conklin (2002).

# Arguments

  * `rpd::RepGame2` : Two player repeated game.
  * `nH::Int` : Number of subgradients used for the approximation.
  * `tol::Float64` : Tolerance in differences of set.
  * `maxiter::Int` : Maximum number of iterations.
  * `check_pure_nash`: Whether to perform a check about whether a pure Nash equilibrium exists.
  * `verbose::Bool` : Whether to display updates about iterations and distance.
  * `nskipprint::Int` : Number of iterations between printing information (assuming verbose=true).
  * `plib::Polyhedra.Library`: Allows users to choose a particular package for the geometry computations. (See [Polyhedra.jl](https://github.com/JuliaPolyhedra/Polyhedra.jl) docs for more info). By default, it chooses to use `CDDLib.Library()`.
  * `lp_solver` : Linear programming solver to be used internally. Pass a `MathOptInterface.AbstractOptimizer` type (such as `HiGHS.Optimizer`) if no option is needed, or a function (such as `GameTheory.highs_optimizer_silent`) to supply options.

# Returns

  * `vertices::Matrix{Float64}` : Vertices of the outer approximation of the value set.
