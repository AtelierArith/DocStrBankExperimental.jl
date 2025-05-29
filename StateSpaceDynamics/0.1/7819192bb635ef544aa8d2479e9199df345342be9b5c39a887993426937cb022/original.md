```
loglikelihood(x::AbstractMatrix{T}, lds::LinearDynamicalSystem{S,O}, y::AbstractMatrix{T}) where {T<:Real, S<:GaussianStateModel{T}, O<:GaussianObservationModel{T}}
```

Calculate the complete-data log-likelihood of a linear dynamical system (LDS) given the observed data.

# Arguments

  * `x::AbstractMatrix{T}`: The state sequence of the LDS.
  * `lds::LinearDynamicalSystem{S,O}`: The Linear Dynamical System.
  * `y::AbstractMatrix{T}`: The observed data.
  * `w::Vector{Float64}`: coeffcients to weight the data.

# Returns

  * `ll::T`: The complete-data log-likelihood of the LDS.
