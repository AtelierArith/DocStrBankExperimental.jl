```
sparse_jacobian(ad::AbstractADType, cache::AbstractMaybeSparseJacobianCache, f, x)
sparse_jacobian(ad::AbstractADType, cache::AbstractMaybeSparseJacobianCache, f!, fx, x)
```

Use the sparsity detection `cache` for computing the sparse Jacobian. This allocates a new Jacobian at every function call.

If `x` is a StaticArray, then this function tries to use a non-allocating implementation for the jacobian computation. This is possible only for a limited backends currently.
