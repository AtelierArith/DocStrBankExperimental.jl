```
diff_conjugate(G::AbstractLieGroup, g, h, X)
diff_conjugate!(G::AbstractLieGroup, Y, g, h, X)
```

Compute the differential of the [`conjugate`](@ref) $c_g(h) = g∘h∘g^{-1}$ on the [`AbstractLieGroup`](@ref) `G`. The operation can be performed in-place of `Y`.

$$
  D(c_g(h))[X], \qquad X ∈ \mathfrak g.
$$
