```
diff_left_compose(G::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, g, h, X)
diff_left_compose!(G::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, Y, g, h, X)
```

Compute the differential of the left group multiplication $λ_g(h) = g∘h$ of the Circle Group, represented as two dimensional vectors in $ℝ^2$.

It simplifies for the [`AbelianMultiplicationGroupOperation`](@ref) to $Dλ_g(h)[X] = g*X$, where the multiplication corresponds to the complex multiplication after canonical identification of the real plane with the complex plane.

This can be computed in-place of `Y`.
