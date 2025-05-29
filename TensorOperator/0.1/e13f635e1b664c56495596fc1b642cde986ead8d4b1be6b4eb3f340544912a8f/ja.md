```
(::Colon)(e₁::BaseTensor{dim},e₂::BaseTensor{dim}) where dim
(::Colon)(t::Tensor{dim},e::BaseTensor{dim}) where dim
(::Colon)(e::BaseTensor{dim},t::Tensor{dim}) where dim
(::Colon)(t₁::Tensor{dim,order_1,N_1},t₂::Tensor{dim,order_2,N_2}) where {dim,order_1,order_2,N_1,N_2}
```

テンソルとベーステンソルのためのダブルドット積。これらの演算子は、次数が2以上のテンソルにのみ適しています。二次テンソルまたはベーステンソル間の演算はスカラー値を返します。他の演算は低次のテンソルまたはベーステンソルを返します。
