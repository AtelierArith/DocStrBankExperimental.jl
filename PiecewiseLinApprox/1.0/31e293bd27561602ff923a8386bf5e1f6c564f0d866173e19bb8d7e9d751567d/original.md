```
SimultaneousLin(expr_fct::Ef,x1::Real,x2::Real, e::ErrorType; ConcavityChanges = [Inf]::Array{Float64,1} )
```

Makes a pair of optimal piecewise Linear underestimation and overestimation of expr_fct from x1 to x2 that share the same breakpoints.

# Arguments

  * `expr_fct` : function to linearize (either an expresion or a native julia function)
  * `x1` : from
  * `x2` : to
  * `e` : error type. Both Absolute() and Relative() are implemented.

# Optional Arguments

  * `ConcavityChanges` : Concavity changes in the function. If not given, they will be computed automatically which, in rare cases, can lead to precision errors if the concavity is asymptotic to zero.

!!! note
    It is also possible to specify which algorithm to use between `HeuristicLin()` and `ExactLin()` by simply adding it after the error type. By default PiecewiseLinApprox uses the heuristic.

