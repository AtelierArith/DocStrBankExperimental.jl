```
StateParams(N::Int, mu::AbstractVector{T}, Phi::Union{AbstractMatrix{T}, UniformScaling}, 
            Omega::Union{AbstractMatrix{T}, UniformScaling}; check_stability::Bool=false) where {T<:Real}
```

Constructs a StateParams instance encapsulating parameters for representing the state-space dynamics of a model.

This constructor accepts both explicit matrices and UniformScaling objects for the state transition component (Phi) and the state noise component (Omega). It enforces that:   • The state mean vector, mu, has length N.   • When Phi is provided as a concrete matrix, it must be of dimensions N×N.   • When Omega is provided as a concrete matrix, it must also be of dimensions N×N.   • Optionally, if the check_stability flag is true, it verifies that the spectral radius of Phi is below 1 - 1e-6,     ensuring the stability of the state transition dynamics.

UniformScaling inputs are converted to explicit N×N matrices to facilitate compatibility with automatic differentiation (AD) and other numerical computations. The function then computes the state covariance matrix, Sigma, as Omega*final * Omega*final'.

# Parameters:

  * N::Int: The number of state variables (dimensionality of the state vector).
  * mu::AbstractVector{T}: The state mean vector; its length must be exactly N.
  * Phi::Union{AbstractMatrix{T}, UniformScaling}: The state transition matrix, provided either as a matrix or as a UniformScaling object.
  * Omega::Union{AbstractMatrix{T}, UniformScaling}: The state noise parameter, provided either as a matrix or as a UniformScaling object.

# Keyword Arguments:

  * check_stability::Bool=false: If set to true, checks that the spectral radius of Phi is less than 1 - 1e-6 to ensure stability.

# Returns:

A StateParams{T} instance containing:     • N: the state dimension.     • mu: the state mean vector.     • Phi*final: the explicit N×N state transition matrix.     • Omega*final: the explicit N×N state noise matrix.     • Sigma: the state covariance matrix computed as Omega*final * Omega*final'.
