```
pseudo_basis(O::AlgAssRelOrd; copy::Bool = true)
```

Returns the pseudo basis of $O$, i. e. a vector $v$ of pairs $(e_i, a_i)$ such that $O = \bigoplus_i a_i e_i$, where $e_i$ is an element of `algebra(O)` and $a_i$ a fractional ideal of `base_ring(O)`.
