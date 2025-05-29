```julia
struct WSOSInterpEpiNormEuclCone{T<:Real} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.WSOSInterpEpiNormEucl`](@ref).

  * `R::Int64`
  * `U::Int64`
  * `Ps::Array{Matrix{T}, 1} where T<:Real`
  * `use_dual::Bool`
