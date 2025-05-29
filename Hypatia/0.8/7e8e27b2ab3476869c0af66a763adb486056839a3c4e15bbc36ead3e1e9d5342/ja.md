```julia
struct GeneralizedPowerCone{T<:Real} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.GeneralizedPower`](@ref).

  * `α::Vector{T} where T<:Real`
  * `n::Int64`
  * `use_dual::Bool`
