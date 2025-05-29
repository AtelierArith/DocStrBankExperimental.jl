```
⋅(e₁::BaseTensor{dim},e₂::BaseTensor{dim}) where dim
⋅(t::Tensor{dim},e::BaseTensor{dim}) where dim
⋅(e::BaseTensor{dim},t::Tensor{dim}) where dim
⋅(t₁::Tensor{dim,order_1,N_1},t₂::Tensor{dim,order_2,N_2}) where {dim,order_1,order_2,N_1,N_2}
```

Dot product for tensors and base tensors. The operations carried between first-order tensors or base tensors will return a scale value. Other operations will return a low order tensor or base tensor.
