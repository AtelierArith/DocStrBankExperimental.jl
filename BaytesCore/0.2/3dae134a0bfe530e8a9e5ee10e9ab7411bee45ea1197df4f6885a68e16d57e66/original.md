```julia
struct TemperingParameter{T<:AbstractFloat}
```

Holds information about updating tempering parameter, parameter for basic logistic function.

# Fields

  * `L::AbstractFloat`
  * `k::AbstractFloat`
  * `x₀::AbstractFloat`
