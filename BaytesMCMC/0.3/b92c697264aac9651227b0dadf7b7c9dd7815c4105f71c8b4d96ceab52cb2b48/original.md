```julia
struct DualAverageParameter{T<:AbstractFloat}
```

Contains information for default Dual Averaging algorithm.

# Fields

  * `δ::AbstractFloat`: Target acceptance rate
  * `γ::AbstractFloat`: Regularization scale
  * `κ::AbstractFloat`: Relaxation exponent - for Average log step size
  * `t₀::Int64`: Offset
