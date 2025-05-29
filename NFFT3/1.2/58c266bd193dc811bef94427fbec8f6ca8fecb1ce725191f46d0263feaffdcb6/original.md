```
nfft_trafo(P::NFFT{D})
```

computes the NDFT via the fast NFFT algorithm for provided nodes $\pmb{x}_j, j =1,2,\dots,M,$ in `P.X` and coefficients $\hat{f}_{\pmb{k}} \in \mathbb{C}, \pmb{k} \in I_{\pmb{N}}^D,$ in `P.fhat`.

# Input

  * `P` - a NFFT plan structure.

# See also

[`NFFT{D}`](@ref), [`nfft_trafo_direct`](@ref)
