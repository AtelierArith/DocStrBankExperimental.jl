```
(l::HashedLocator)(x,t)
```

Estimate the parameter value `uv⁺ = argmin_uv (X-curve(uv,t))²` in two steps:

1. Interploate an initial guess  `uv=l.hash(x)`. Return `uv⁺~uv` if `x` is outside the hash domain.
2. Apply a bounded Newton step `uv⁺≈l.refine(x,uv,t)` to refine the estimate.
