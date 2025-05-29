```
SmoothLP(names, order::Int=3, ndiff::Int=3; kwargs)
```

Constructor for [`SmoothLP`](@ref).

# Arguments

  * `names`: column indices of variables from the data table to be fit with penalized splines.
  * `order`: the highest order of the polynomial term in a spline basis.
  * `ndiff`: the order of the finite difference operator used to penalize B-spline coefficients.

# Keywords

  * `search::ModelSelection=grid()`: method for generating alternative smoothing parameters.
  * `criterion::SearchCriterion=LOOCV()`: criterion for selecting the optimal parameter.
  * `fullX::Bool=false`: whether regressor matrices not involved in smoothing are kept.
