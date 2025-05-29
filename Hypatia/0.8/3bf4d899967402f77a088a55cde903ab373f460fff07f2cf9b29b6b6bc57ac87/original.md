```julia
struct EpiPerSepSpectralCone{T<:Real} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.EpiPerSepSpectral`](@ref).

  * `h::Hypatia.Cones.SepSpectralFun`
  * `Q::Type{<:Hypatia.Cones.ConeOfSquares{T}} where T<:Real`
  * `d::Int64`
  * `use_dual::Bool`
