```
diff_right_compose(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, g, h, X)
diff_right_compose(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, Y, g, h, X)
```

Compute the differential of the right group multiplication $ρ_g(h) = h∘g$. On the complex circle the differential simplifies to the ordinary complex multiplication

$$
    ρ_g(h) = X ⋅ g.
$$

This can be computed in-place of `Y` if `Y` is `mutable` due to the wrapper defined in the [`AbelianMultiplicationGroupOperation`](@ref).
