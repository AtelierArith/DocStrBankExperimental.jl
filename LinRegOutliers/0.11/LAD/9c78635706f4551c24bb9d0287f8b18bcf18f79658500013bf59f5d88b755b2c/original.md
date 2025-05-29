```
lad(X, y, exact = true)
```

Perform Least Absolute Deviations regression for a given regression setting.

# Arguments

  * `X::AbstractMatrix{Float64}`: Design matrix of the linear model.
  * `y::AbstractVector{Float64}`: Response vector of the linear model.
  * `exact::Bool`: If true, use exact LAD regression. If false, estimate LAD regression parameters using GA. Default is true.
