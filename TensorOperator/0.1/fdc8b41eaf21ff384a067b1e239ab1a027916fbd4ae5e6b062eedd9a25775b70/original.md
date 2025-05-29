```
⊗(e₁::BaseTensor{dim},e₂::BaseTensor{dim}) where dim
⊗(t::Tensor{dim},e::BaseTensor{dim}) where dim
⊗(e::BaseTensor{dim},t::Tensor{dim}) where dim
⊗(t₁::Tensor{dim,order_1,N_1},t₂::Tensor{dim,order_2,N_2}) where {dim,order_1,order_2,N_1,N_2}
```

Dyadic operaotrs for tensors and base tensors. Inputing two base tensors returns a high order base tensor. Inputing at least one tensor returns a tensor with high order base tensors.
