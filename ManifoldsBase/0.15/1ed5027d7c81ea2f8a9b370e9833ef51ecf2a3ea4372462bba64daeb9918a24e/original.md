```
vee(M::AbstractManifold, p, X)
```

Given a basis $e_i$ on the tangent space at a point `p` and tangent vector `X`, compute the vector components $X^i ∈ ℝ$, such that $X = X^i e_i$, where Einstein summation notation is used:

$$
\vee : X^i e_i ↦ X^i
$$

For array manifolds, this converts an array representation of the tangent vector to a vector representation. The [`hat`](@ref) map is the `vee` map's inverse.
