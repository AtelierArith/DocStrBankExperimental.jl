```julia
struct HypoPerLogdetTriCone{T<:Real, R<:Union{Complex{T<:Real}, T<:Real}} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.HypoPerLogdetTri`](@ref).

  * `dim::Int64`
  * `use_dual::Bool`
