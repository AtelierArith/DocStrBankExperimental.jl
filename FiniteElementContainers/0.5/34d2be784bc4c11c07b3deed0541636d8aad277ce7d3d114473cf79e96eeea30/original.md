```julia
modify_field_gradients(
    _::FiniteElementContainers.PlaneStrain,
    ∇u_q::StaticArraysCore.SArray{Tuple{2, 2}, T<:Number, 2, 4},
    _::Type{<:Tensors.Tensor}
) -> Tensors.Tensor{2, 3, _A, 9} where _A

```
