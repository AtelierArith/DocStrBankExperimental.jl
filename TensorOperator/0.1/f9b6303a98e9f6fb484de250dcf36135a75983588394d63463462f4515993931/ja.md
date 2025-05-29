```
⋅(e₁::BaseTensor{dim},e₂::BaseTensor{dim}) where dim
⋅(t::Tensor{dim},e::BaseTensor{dim}) where dim
⋅(e::BaseTensor{dim},t::Tensor{dim}) where dim
⋅(t₁::Tensor{dim,order_1,N_1},t₂::Tensor{dim,order_2,N_2}) where {dim,order_1,order_2,N_1,N_2}
```

テンソルとベーステンソルのドット積。一次元テンソルまたはベーステンソル間で行われる演算はスケール値を返します。他の演算は低次元テンソルまたはベーステンソルを返します。
