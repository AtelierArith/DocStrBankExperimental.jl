```
log(M::AbstractSphere, p, q)
```

Compute the logarithmic map on the [`AbstractSphere`](@ref) `M`, i.e. the tangent vector, whose geodesic starting from `p` reaches `q` after time 1. The formula reads for $x ≠ -y$

$$
\log_p q = d_{𝕊}(p,q) \frac{q-\Re(⟨p,q⟩) p}{\lVert q-\Re(⟨p,q⟩) p \rVert_2},
$$

and a deterministic choice from the set of tangent vectors is returned if $x=-y$, i.e. for opposite points.
