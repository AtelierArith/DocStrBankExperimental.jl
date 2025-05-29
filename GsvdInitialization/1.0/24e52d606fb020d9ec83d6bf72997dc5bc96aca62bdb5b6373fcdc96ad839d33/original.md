```
W, H = gsvdnmf(X::AbstractMatrix, W::AbstractMatrix, H::AbstractMatrix, f;
               n2 = size(first(f), 2),
               tol_nmf=1e-4,
               kwargs...)
```

Augment `W` and `H` to have `n2` components, subsequently polished by NMF.

Arguments:

  * `X`: non-negative data matrix
  * `W` and `H`: initial NMF factorization
  * `n2`: the number of components in augmented factorization
  * `f`: SVD (or Truncated SVD) of `X`

Keyword arguments:

  * `tol_nmf`: the tolerance of  NMF polishing step, default: 1e-4

Other keyword arguments are passed to `NMF.nnmf`.
