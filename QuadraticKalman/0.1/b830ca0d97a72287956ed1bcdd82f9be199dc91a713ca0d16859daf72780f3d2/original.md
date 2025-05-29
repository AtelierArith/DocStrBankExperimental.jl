```
MeasParams(M::Int, N::Int, A::AbstractVector{T}, 
           B::Union{AbstractMatrix{T}, UniformScaling},
           C::Vector{<:Union{AbstractMatrix{T}, UniformScaling}}, 
           D::Union{AbstractMatrix{T}, UniformScaling},
           alpha::Union{AbstractMatrix{T}, UniformScaling}) where {T<:Real}
```

Constructs a MeasParams object containing the parameters for the measurement equation in a quadratic state-space model.

# Arguments

  * M::Int: The number of measurement variables.
  * N::Int: The number of state variables.
  * A::AbstractVector{T}: A vector of intercept terms in the measurement equation. Its length must equal M.
  * B::Union{AbstractMatrix{T}, UniformScaling}: The matrix mapping the state vector to the measurement space. If provided as a UniformScaling, it is converted to an M×N matrix.
  * C::Vector{<:Union{AbstractMatrix{T}, UniformScaling}}: A vector of matrices representing the quadratic measurement parameters. There must be M matrices, each of size N×N. UniformScaling inputs are converted accordingly.
  * D::Union{AbstractMatrix{T}, UniformScaling}: A matrix scaling the measurement noise, required to be M×M. UniformScaling inputs are converted to a standard matrix.
  * alpha::Union{AbstractMatrix{T}, UniformScaling}: A matrix capturing the autoregressive component in the measurement equation. If provided as UniformScaling, it is converted to an M×M matrix.

# Returns

A MeasParams object parameterized by type T, encapsulating all measurement model parameters, along with an auxiliary matrix V computed as V = D*final * D*final', which represents the covariance structure of the measurement noise.

# Details

This function ensures that all inputs are represented as concrete matrices, even when provided as UniformScaling objects. For B and each element in C, as well as D and alpha, if the input is a UniformScaling, it is converted into a full matrix with the appropriate dimensions (M×N for B, N×N for each Ci in C, and M×M for D and alpha). This conversion guarantees compatibility with downstream operations in filtering and smoothing routines, which require complete matrix representations for accurate linear algebra computations.
