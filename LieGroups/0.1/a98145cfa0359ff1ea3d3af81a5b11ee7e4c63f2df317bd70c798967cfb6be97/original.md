```
diff_inv(G::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, g, X)
diff_inv!(G::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, Y, g, X)
```

Compute the the differential $Dι_{\mathcal G}([g])[X]$ of the inversion $ι_{\mathcal G}([g]) := [g]^{-1} = [-g]$ at $X ∈ 𝔤$ in the [`LieAlgebra`](@ref) $𝔤$ of the [real `CircleGroup`](@ref circle-group-real) `G` $=\mathcal G$.

The computation simplifies due to commutativity to

$$
Dι_{\mathcal G}([g])[X] = -X.
$$

This can be computed in-place of `Y` if `Y` is `mutable`.
