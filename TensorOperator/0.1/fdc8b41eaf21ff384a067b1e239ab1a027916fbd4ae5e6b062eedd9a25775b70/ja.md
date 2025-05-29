```
⊗(e₁::BaseTensor{dim},e₂::BaseTensor{dim}) where dim
⊗(t::Tensor{dim},e::BaseTensor{dim}) where dim
⊗(e::BaseTensor{dim},t::Tensor{dim}) where dim
⊗(t₁::Tensor{dim,order_1,N_1},t₂::Tensor{dim,order_2,N_2}) where {dim,order_1,order_2,N_1,N_2}
```

テンソルとベーステンソルのための二項演算子。2つのベーステンソルを入力すると、高次のベーステンソルが返されます。少なくとも1つのテンソルを入力すると、高次のベーステンソルを持つテンソルが返されます。
