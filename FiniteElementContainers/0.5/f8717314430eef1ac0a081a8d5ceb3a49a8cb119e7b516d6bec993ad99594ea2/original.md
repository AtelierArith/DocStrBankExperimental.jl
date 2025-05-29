```julia
modify_field_gradients(
    _::FiniteElementContainers.IncompressiblePlaneStress,
    ∇u_q::Tensors.Tensor{2, 2, T<:Number, 4},
    _::Type{<:Tensors.Tensor}
) -> Tensors.Tensor{2, 3, _A, 9} where _A

```
