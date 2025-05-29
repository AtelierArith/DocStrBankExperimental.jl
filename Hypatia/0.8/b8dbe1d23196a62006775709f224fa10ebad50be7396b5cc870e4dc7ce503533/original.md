```julia
struct HypoRootdetTriCone{T<:Real, R<:Union{Complex{T<:Real}, T<:Real}} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.HypoRootdetTri`](@ref).

  * `dim::Int64`
  * `use_dual::Bool`
