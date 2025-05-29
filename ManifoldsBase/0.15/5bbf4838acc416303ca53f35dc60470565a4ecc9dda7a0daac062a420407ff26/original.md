```
norm(M::AbstractPowerManifold, p, X, r::Real=2)
```

Compute the norm of `X` from the tangent space of `p` on an [`AbstractPowerManifold`](@ref) `M`, i.e. from the element wise norms `r`-norm is computed, where the default `r=2` yields the Frobenius norm is computed.
