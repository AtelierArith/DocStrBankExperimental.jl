```
nfmt_trafo(P)
```

computes the NDMT via the fast NFMT algorithm for provided nodes $\pmb{x}_j, j =1,2,\dots,M,$ in `P.X` and coefficients $\hat{f}_{\pmb{k}}^{\pmb{d}} \in \mathbb{R}, \pmb{k} \in I_{\pmb{N},\pmb{d}}^D,$ in `P.fhat`.

# Input

  * `P` - a NFMT plan structure.

# See also

[`NFMT{D}`](@ref), [`nfmt_trafo_direct`](@ref)
