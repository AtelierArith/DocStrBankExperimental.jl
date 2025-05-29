```julia
modify_field_gradients(
    _::FiniteElementContainers.PlaneStrain,
    ∇u_q::StaticArraysCore.SArray{Tuple{2, 2}, T<:Number, 2, 4},
    _::Type{<:StaticArraysCore.SArray}
) -> StaticArraysCore.SArray

```
