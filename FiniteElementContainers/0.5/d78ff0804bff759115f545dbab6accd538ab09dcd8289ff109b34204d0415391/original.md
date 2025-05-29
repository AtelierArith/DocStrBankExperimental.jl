To deprecate or not to deprecate?

```julia
modify_field_gradients(
    form::FiniteElementContainers.PlaneStrain,
    ∇u_q::StaticArraysCore.SArray{Tuple{2, 2}, T<:Number, 2, 4};
    type
) -> Tensors.Tensor{2, 3, _A, 9} where _A

```
