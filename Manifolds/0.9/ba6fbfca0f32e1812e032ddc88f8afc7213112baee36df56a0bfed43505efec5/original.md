```
log(M::Hyperbolic, p, q)
```

Compute the logarithmic map on the [`Hyperbolic`](@ref) space $\mathcal H^n$, the tangent vector representing the [`geodesic`](@extref `ManifoldsBase.geodesic-Tuple{AbstractManifold, Any, Any}`) starting from `p` reaches `q` after time 1. The formula reads for $p ≠ q$

$$
\log_p q = d_{\mathcal H^n}(p,q)
\frac{q-⟨p,q⟩_{\mathrm{M}} p}{\lVert q-⟨p,q⟩_{\mathrm{M}} p \rVert_2},
$$

where $⟨⋅,⋅⟩_{\mathrm{M}}$ denotes the [`MinkowskiMetric`](@ref) on the embedding, the [`Lorentz`](@ref)ian manifold. For $p=q$ the logarithmic map is equal to the zero vector.
