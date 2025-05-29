```julia
struct EpiNormSpectralCone{T<:Real, R<:Union{Complex{T<:Real}, T<:Real}} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.EpiNormSpectral`](@ref).

  * `d1::Int64`
  * `d2::Int64`
  * `use_dual::Bool`
