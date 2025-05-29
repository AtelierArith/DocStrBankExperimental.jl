```
diff_right_compose(G::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, g, h, X)
diff_right_compose!(G::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, Y, g, h, X)
```

Compute the differential of the right group multiplication $λ_g(h) = g∘h$ of the Circle Group, represented as two dimensional vectors in $ℝ^2$.

It simplifies for the [`AbelianMultiplicationGroupOperation`](@ref) to $Dλ_g(h)[X] = X*g$, where the multiplication corresponds to the complex multiplication after canonical identification of the real plane with the complex plane.
