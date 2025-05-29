```julia
struct HypoPerLogCone{T<:Real} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.HypoPerLog`](@ref).

  * `dim::Int64`
  * `use_dual::Bool`
