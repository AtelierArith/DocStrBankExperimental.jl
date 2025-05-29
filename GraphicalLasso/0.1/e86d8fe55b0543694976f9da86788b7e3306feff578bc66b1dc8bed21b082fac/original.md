```
cdlasso(W11::Matrix{T}, s12::Vector{T}, λ::Real; max_iter::Int=100, tol::T=1e-5) where {T<:Real}
```

Solves the coordinate descent Lasso problem.

# Arguments

  * `W11::Matrix{T}`: A square matrix used in the coordinate descent update.
  * `s12::Vector{T}`: A vector used in the coordinate descent update.
  * `λ::Real`: Regularization parameter.
  * `max_iter::Int=100`: Maximum number of iterations. (optional)
  * `tol::T=1e-5`: Tolerance for the convergence criteria. (optional)

# Returns

  * `Vector{T}`: Solution vector `β`.
