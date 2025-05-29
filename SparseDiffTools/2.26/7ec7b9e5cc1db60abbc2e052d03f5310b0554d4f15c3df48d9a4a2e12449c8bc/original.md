```
sparse_jacobian(ad::AbstractADType, sd::AbstractMaybeSparsityDetection, f, x; fx=nothing)
sparse_jacobian(ad::AbstractADType, sd::AbstractMaybeSparsityDetection, f!, fx, x)
```

Sequentially calls `sparse_jacobian_cache` and `sparse_jacobian!` to compute the Jacobian of `f` at `x`. Use this if the jacobian for `f` is computed exactly once. In all other cases, use `sparse_jacobian_cache` once to generate the cache and use `sparse_jacobian!` with the same cache to compute the jacobian.

If `x` is a StaticArray, then this function tries to use a non-allocating implementation for the jacobian computation. This is possible only for a limited backends currently.
