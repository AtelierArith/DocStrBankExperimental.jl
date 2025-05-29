```julia
struct EpiNormInfCone{T<:Real, R<:Union{Complex{T<:Real}, T<:Real}} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.EpiNormInf`](@ref).

  * `dim::Int64`
  * `use_dual::Bool`
