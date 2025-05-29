```
project(M::OrthogonalMatrices, p, X)
project(M::Rotations, p, X)
project(M::UnitaryMatrices, p, X)
```

Orthogonally project the tangent vector $X ∈ 𝔽^{n×n}$, $\mathbb F ∈ \{\mathbb R, \mathbb C\}$ to the tangent space of `M` at `p`, and change the representer to use the corresponding Lie algebra, i.e. we compute

$$
    \operatorname{proj}_p(X) = \frac{p^{\mathrm{H}} X - (p^{\mathrm{H}} X)^{\mathrm{H}}}{2},
$$
