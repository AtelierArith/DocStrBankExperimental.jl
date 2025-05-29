```
init_jacobian(cache::AbstractMaybeSparseJacobianCache;
    preserve_immutable::Val = Val(false))
```

Initialize the Jacobian based on the cache. Uses sparse jacobians if possible.

If `preserve_immutable` is `true`, then the Jacobian returned might be immutable, this is relevant if the inputs are immutable like `StaticArrays`.
