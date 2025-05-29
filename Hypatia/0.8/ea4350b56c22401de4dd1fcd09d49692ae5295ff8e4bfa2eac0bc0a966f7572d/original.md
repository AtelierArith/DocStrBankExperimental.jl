```julia
struct EpiTrRelEntropyTriCone{T<:Real, R<:Union{Complex{T<:Real}, T<:Real}} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.EpiTrRelEntropyTri`](@ref).

  * `dim::Int64`
  * `use_dual::Bool`
