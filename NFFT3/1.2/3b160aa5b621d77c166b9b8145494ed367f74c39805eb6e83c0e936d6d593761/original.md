```
nfft_trafo_direct(P::NFFT{D})
```

computes the NDFT via naive matrix-vector multiplication for provided nodes $\pmb{x}_j, j =1,2,\dots,M,$ in `P.X` and coefficients $\hat{f}_{\pmb{k}} \in \mathbb{C}, \pmb{k} \in I_{\pmb{N}}^D,$ in `P.fhat`.

# Input

  * `P` - a NFFT plan structure.

# See also

[`NFFT{D}`](@ref), [`nfft_trafo`](@ref)
