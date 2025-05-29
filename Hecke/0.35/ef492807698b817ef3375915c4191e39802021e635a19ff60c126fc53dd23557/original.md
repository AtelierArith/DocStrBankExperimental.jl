```
hnf_modular(M::MatElem{T}, d::T, is_prime::Bool = false)
```

Return the `hnf` of `vcat(M, identity_matrix(parent(d), ncols(M)))` if `is_prime` is set, then instead of an `hnf` internally a `rref` over the residue field modulo `d` is used.
