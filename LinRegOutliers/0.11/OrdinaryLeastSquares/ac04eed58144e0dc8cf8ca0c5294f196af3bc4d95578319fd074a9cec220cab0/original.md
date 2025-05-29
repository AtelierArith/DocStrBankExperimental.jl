```
struct OLS
    X::AbstractMatrix{Float64}
    y::AbstractVector{Float64}
    betas::AbstractVector{Float64}
end 

Immutable data structure that holds design matrix, response vector, and estimated regression parameters.
```

# Arguments

  * `X::AbstractMatrix{Float64}`: Design matrix.
  * `y::AbstractVector{Float64}`: Response vector.
  * `betas::AbstractVector{Float64}`: Regression coefficients.
