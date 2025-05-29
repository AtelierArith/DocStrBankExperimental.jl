```
tuningselect(s::Matrix{Float64}, obs::Int, λ::AbstractVector{T}; γ::Real=0.0) where {T}
```

Selects the optimal regularization parameter `λ` for the graphical lasso using EBIC.

# Arguments

  * `s::Matrix{Float64}`: Empirical covariance matrix.
  * `obs::Int`: Number of observations.
  * `λ::AbstractVector{T}`: Vector of regularization parameters to be tested.
  * `γ::Real=0.0`: EBIC tuning parameter. (optional)

# Returns

  * `T`: The optimal regularization parameter from the input vector `λ`.
