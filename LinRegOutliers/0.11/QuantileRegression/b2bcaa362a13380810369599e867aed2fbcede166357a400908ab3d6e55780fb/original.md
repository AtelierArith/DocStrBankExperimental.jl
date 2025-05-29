```
quantileregression(X, y, tau = 0.5)
```

Estimates parameters of linear regression using Quantile Regression Estimator for a given regression setting.

# Arguments

  * `X::AbstractMatrix{Float64}`: Design matrix of the linear model.
  * `y::AbstractVector{Float64}`: Response vector of the linear model.
  * `tau::Float64`: Quantile level. Default is 0.5.

# Examples

```julia-repl
julia> income = [420.157651, 541.411707, 901.157457, 639.080229, 750.875606];
julia> foodexp = [255.839425, 310.958667, 485.680014, 402.997356, 495.560775];

julia> n = length(income)
julia> X = hcat(ones(Float64, n), income)

julia> result = quantileregression(X, foodexp, tau = 0.25)
```
