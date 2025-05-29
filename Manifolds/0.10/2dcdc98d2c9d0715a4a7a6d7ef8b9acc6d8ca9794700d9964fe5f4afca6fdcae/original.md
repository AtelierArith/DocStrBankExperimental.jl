```
inner(B::VectorBundle, p, X, Y)
```

Inner product of tangent vectors `X` and `Y` at point `p` from the vector bundle `B` over manifold `B.fiber` (denoted $\mathcal M$).

Notation:

  * The point $p = (x_p, V_p)$ where $x_p ∈ \mathcal M$ and $V_p$ belongs to the fiber $F=π^{-1}(\{x_p\})$ of the vector bundle $B$ where $π$ is the canonical projection of that vector bundle $B$.
  * The tangent vector $v = (V_{X,M}, V_{X,F}) ∈ T_{x}B$ where $V_{X,M}$ is a tangent vector from the tangent space $T_{x_p}\mathcal M$ and $V_{X,F}$ is a tangent vector from the tangent space $T_{V_p}F$ (isomorphic to $F$). Similarly for the other tangent vector $w = (V_{Y,M}, V_{Y,F}) ∈ T_{x}B$.

The inner product is calculated as

$⟨X, Y⟩_p = ⟨V_{X,M}, V_{Y,M}⟩_{x_p} + ⟨V_{X,F}, V_{Y,F}⟩_{V_p}.$
