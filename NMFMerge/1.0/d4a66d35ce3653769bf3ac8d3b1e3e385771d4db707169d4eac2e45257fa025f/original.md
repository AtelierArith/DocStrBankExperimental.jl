```
result = nmfmerge(X, ncomponents; tol_final=1e-4, tol_intermediate=sqrt(tol_final), W0=nothing, H0=nothing, kwargs...)
```

Performs "NMF-Merge" on data matrix `X`.

Arguments:

  * `X::AbstractMatrix`: the data matrix to be factorized
  * `ncomponents::Pair{Int,Int}`: in the form of `n1 => n2`, merging from `n1` components to `n2`components, where `n1` is the number of components for overcomplete NMF, and `n2` is the number of components for the final NMF. We require `n1 >= n2`.

Alternatively, `ncomponents` can be an integer denoting the final number of components. In this case, `nmfmerge` defaults to an approximate 20% component excess before merging.

Keyword arguments:

  * `tol_final`: The tolerance of final NMF
  * `tol_intermediate`: The tolerence of initial and overcomplete NMF

`W0`, `H0`: initialization for the initial NMF. If at least one of `W0` and `H0` is `nothing`, NNDSVD is used for initialization.

Other keywords arguments are passed to `NMF.nnmf`.
