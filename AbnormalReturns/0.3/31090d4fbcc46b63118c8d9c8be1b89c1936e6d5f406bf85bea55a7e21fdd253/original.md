```
function BasicReg(
    resp::AbstractVector,
    pred::AbstractMatrix,
    yname::String,
    xnames::SVector{N, String},
    f::FormulaTerm{L,R};
    save_residuals::Bool=false,
    minobs=1
)::BasicReg{L,R} where {L,R}
```

## Arguments

  * resp::AbstractVector{Float64}: The "Y" or response in a linear regression
  * pred::AbstractMatrix{Float64}: The "X" matrix in a linear regression
  * yname::String: The name of the response variable
  * xnames::SVector{N, String}: The names of the prediction variables
  * f::FormulaTerm{L,R}: A StatsModels.jl formula, saved in the resulting struct
  * save_residuals::Bool=false: Whether or not to save the vector of residuals from   the regression. Note for large numbers of regressions this can significantly slow   down the speed
  * minobs::Int=1: The minimum length of the response vector for the regression to   run. The regression will also not run if the length of the response vector is   less than or equal to the number of columns in the prediction matrix.

BasicReg is an intentionally simplistic linear regression. It also attempts to produce a minimum number of allocations if views of vectors are passed.
