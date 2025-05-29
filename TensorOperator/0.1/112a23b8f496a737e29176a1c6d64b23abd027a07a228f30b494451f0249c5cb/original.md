```
×(v₁::Tuple{Vararg{T,3}},v₂::Tuple{Vararg{T,3}}) where T
×(e₁::BaseTensor{3},e₂::BaseTensor{3})
×(t::Tensor{dim},e::BaseTensor{dim}) where dim
×(e::BaseTensor{dim},t::Tensor{dim}) where dim
×(t₁::Tensor{dim,order_1,N_1},t₂::Tensor{dim,order_2,N_2}) where {dim,order_1,order_2,N_1,N_2}
```

Cross product for tensors and base tensors. These operaotrs only suit for the tensors that their order greater than or equal to 2. The operations between second-order tensors or base tensors will return a scale value. Other operations will return a low order tensor or base tensor.
