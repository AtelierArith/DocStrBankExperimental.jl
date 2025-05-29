```
diff_left_compose(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, g, h, X)
diff_left_compose(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, Y, g, h, X)
```

Compute the differential of the left group multiplication $λ_g(h) = g∘h$. On the complex circle the differential simplifies to the ordinary complex multiplication

$$
    λ_g(h) = g ⋅ X.
$$

This can be computed in-place of `Y` if `Y` is `mutable`.
