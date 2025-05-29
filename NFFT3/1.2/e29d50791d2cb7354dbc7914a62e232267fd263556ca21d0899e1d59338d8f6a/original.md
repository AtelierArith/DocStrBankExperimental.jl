```
nfct_transposed(P)
```

computes the transposed NDCT via the fast transposed NFCT algorithm for provided nodes $\pmb{x}_j, j =1,2,\dots,M,$ in `P.X` and coefficients $f_j^c \in \mathbb{R}, j =1,2,\dots,M,$ in `P.f`.

# Input

  * `P` - a NFCT plan structure.

# See also

[`NFCT{D}`](@ref), [`nfct_transposed_direct`](@ref)
