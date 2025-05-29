```julia
struct LinMatrixIneqCone{T<:Real} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.LinMatrixIneq`](@ref).

  * `As::Vector`
  * `use_dual::Bool`
