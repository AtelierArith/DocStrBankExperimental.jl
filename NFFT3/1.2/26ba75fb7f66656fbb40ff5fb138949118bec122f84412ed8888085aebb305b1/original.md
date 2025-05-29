```
nfct_trafo_direct(P)
```

computes the NDCT via naive matrix-vector multiplication for provided nodes $\pmb{x}_j, j =1,2,\dots,M,$ in `P.X` and coefficients $\hat{f}_{\pmb{k}}^c \in \mathbb{R}, \pmb{k} \in I_{\pmb{N},\mathrm{c}}^D,$ in `P.fhat`.

# Input

  * `P` - a NFCT plan structure.

# See also

[`NFCT{D}`](@ref), [`nfct_trafo`](@ref)
