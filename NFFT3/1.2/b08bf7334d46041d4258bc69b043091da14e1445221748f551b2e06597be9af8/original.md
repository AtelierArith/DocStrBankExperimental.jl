```
nfst_trafo_direct(P)
```

computes the NDST via naive matrix-vector multiplication for provided nodes $\pmb{x}_j, j =1,2,\dots,M,$ in `P.X` and coefficients $\hat{f}_{\pmb{k}}^s \in \mathbb{R}, \pmb{k} \in I_{\pmb{N},s}^D,$ in `P.fhat`.

# Input

  * `P` - a NFST plan structure.

# See also

[`NFST{D}`](@ref), [`nfst_trafo`](@ref)
