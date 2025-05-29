```julia
struct DoublyNonnegativeTriCone{T<:Real} <: MathOptInterface.AbstractVectorSet
```

See [`Cones.DoublyNonnegativeTri`](@ref).

  * `dim::Int64`
  * `use_dual::Bool`
