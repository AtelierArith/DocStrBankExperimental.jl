```
nfft_adjoint(P::NFFT{D})
```

computes the adjoint NDFT via the fast adjoint NFFT algorithm for provided nodes $\pmb{x}_j, j =1,2,\dots,M,$ in `P.X` and coefficients $f_j \in \mathbb{C}, j =1,2,\dots,M,$ in `P.f`.

# Input

  * `P` - a NFFT plan structure.

# See also

[`NFFT{D}`](@ref), [`nfft_adjoint_direct`](@ref)
