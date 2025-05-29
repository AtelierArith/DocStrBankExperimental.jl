```julia
struct WSOSInterpNonnegativeCone{T<:Real, R<:Union{Complex{T<:Real}, T<:Real}} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.WSOSInterpNonnegative`](@ref).

  * `U::Int64`
  * `Ps::Array{Matrix{R}, 1} where {T<:Real, R<:Union{Complex{T}, T}}`
  * `use_dual::Bool`
