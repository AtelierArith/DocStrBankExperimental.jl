```julia
struct EpiNormSpectralTriCone{T<:Real, R<:Union{Complex{T<:Real}, T<:Real}} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.EpiNormSpectralTri`](@ref).

  * `dim::Int64`
  * `use_dual::Bool`
