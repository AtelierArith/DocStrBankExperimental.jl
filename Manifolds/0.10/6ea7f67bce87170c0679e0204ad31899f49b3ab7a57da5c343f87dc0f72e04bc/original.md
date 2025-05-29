```
inner(M::GeneralizedStiefel, p, X, Y)
```

Compute the inner product for two tangent vectors `X`, `Y` from the tangent space of `p` on the [`GeneralizedStiefel`](@ref) manifold `M`. The formula reads

$$
(X, Y)_p = \operatorname{trace}(v^{\mathrm{H}}Bw),
$$

i.e. the metric induced by the scalar product `B` from the embedding, restricted to the tangent space.
