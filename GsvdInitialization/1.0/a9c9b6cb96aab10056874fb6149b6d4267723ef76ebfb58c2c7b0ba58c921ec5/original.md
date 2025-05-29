```
W, H = gsvdnmf(X::AbstractMatrix, ncomponents::Pair{Int,Int}; tol_final=1e-4, tol_intermediate=1e-4, kwargs...)
```

Perform "GSVD-NMF" on the data matrix `X`.

Arguments:

  * `X`: non-negative data matrix
  * `ncomponents`: in the form of `n1 => n2`, augments from `n1` components to `n2`components, where `n1` is the number of components for initial NMF (under-complete NMF), and `n2` is the number of components for final NMF.

Alternatively, `ncomponents` can be an integer denoting the number of components for final NMF. In this case, `gsvdnmf` defaults to augment components on initial NMF solution by 1.

Keyword arguments:

  * `tol_final`: The tolerence of final NMF, default:`10^{-4}`
  * `tol_intermediate`: The tolerence of initial NMF (under-complete NMF), default: tol_final

Other keyword arguments are passed to `NMF.nnmf`.
