```
init_jacobian(cache::AbstractMaybeSparseJacobianCache)
```

Initialize the Jacobian based on the cache. Uses sparse jacobians if possible.

!!! note
    This function doesn't alias the provided jacobian prototype. It always initializes a fresh jacobian that can be mutated without any side effects.

