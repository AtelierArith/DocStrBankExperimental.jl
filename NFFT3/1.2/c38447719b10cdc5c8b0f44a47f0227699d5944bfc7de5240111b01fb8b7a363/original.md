```
nfft_adjoint_direct(P::NFFT{D})
```

computes the adjoint NDFT via naive matrix-vector multiplication for provided nodes $\pmb{x}_j, j =1,2,\dots,M,$ in `P.X` and coefficients $f_j \in \mathbb{C}, j =1,2,\dots,M,$ in `P.f`.

# Input

  * `P` - a NFFT plan structure.

# See also

[`NFFT{D}`](@ref), [`nfft_adjoint`](@ref)
