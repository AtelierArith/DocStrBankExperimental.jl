```julia
struct HypoPowerMeanCone{T<:Real} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.HypoPowerMean`](@ref).

  * `α::Vector{T} where T<:Real`
  * `use_dual::Bool`
