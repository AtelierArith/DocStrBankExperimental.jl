```
pseudo_basis(a::AlgAssRelOrdIdl; copy::Bool = true)
```

Returns the pseudo basis of $a$, i. e. a vector $v$ of pairs $(e_i, a_i)$ such that $a = \bigoplus_i a_i e_i$, where $e_i$ is an element of `algebra(a)` and $a_i$ is a fractional ideal of `base_ring(left_order(a))`.
