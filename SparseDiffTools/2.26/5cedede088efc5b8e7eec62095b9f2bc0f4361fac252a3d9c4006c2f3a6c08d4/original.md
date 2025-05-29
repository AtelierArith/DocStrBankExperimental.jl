```
sparse_jacobian_cache(ad::AbstractADType, sd::AbstractSparsityDetection, f, x;
    fx=nothing)
sparse_jacobian_cache(ad::AbstractADType, sd::AbstractSparsityDetection, f!, fx, x)
```

Takes the underlying AD backend `ad`, sparsity detection algorithm `sd`, function `f`, and input `x` and returns a cache object that can be used to compute the Jacobian.

If `fx` is not specified, it will be computed by calling `f(x)`.

## Returns

A cache for computing the Jacobian of type `AbstractMaybeSparseJacobianCache`.
