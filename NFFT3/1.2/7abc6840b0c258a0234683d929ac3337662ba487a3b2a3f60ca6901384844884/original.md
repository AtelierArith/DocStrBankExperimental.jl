```
nfmt_transposed(P)
```

computes the transposed NDFCT via the fast transposed NFMT algorithm for provided nodes $\pmb{x}_j, j =1,2,\dots,M,$ in `P.X` and coefficients $f_j^{\pmb{d}} \in \mathbb{R}, j =1,2,\dots,M,$ in `P.f`.

# Input

  * `P` - a NFMT plan structure.

# See also

[`NFMT{D}`](@ref), [`nfmt_transposed_direct`](@ref)
