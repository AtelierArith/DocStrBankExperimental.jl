```
diff_conjugate(G::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, g, h, X)
diff_conjugate!(G::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, Y, g, h, X)
```

Compute the differential of the [conjugation map](@ref conjugate) $c_g(h) = g∘h∘g^{-1}=h$. On the circle group represented as [part of the real line](@ref circle-group-real), this simplifies to $D(c_g(h))[X] = X$.

This can be computed in-place of `Y` if `Y` is `mutable`.
