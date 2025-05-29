```
sparse_jacobian!(J::AbstractMatrix, ad, cache::AbstractMaybeSparseJacobianCache, f, x)
sparse_jacobian!(J::AbstractMatrix, ad, cache::AbstractMaybeSparseJacobianCache, f!, fx,
    x)
```

Inplace update the matrix `J` with the Jacobian of `f` at `x` using the AD backend `ad`.

`cache` is the cache object returned by `sparse_jacobian_cache`.
