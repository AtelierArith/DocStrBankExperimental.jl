```
zero_vector(B::FiberBundle, p)
```

Zero tangent vector at point `p` from the fiber bundle `B` over manifold `B.fiber` (denoted $\mathcal M$). The zero vector belongs to the space $T_{p}B$

Notation:

  * The point $p = (x_p, V_p)$ where $x_p ∈ \mathcal M$ and $V_p$ belongs to the fiber $F=π^{-1}(\{x_p\})$ of the vector bundle $B$ where $π$ is the canonical projection of that vector bundle $B$.

The zero vector is calculated as

$\mathbf{0}_{p} = (\mathbf{0}_{x_p}, \mathbf{0}_F)$

where $\mathbf{0}_{x_p}$ is the zero tangent vector from $T_{x_p}\mathcal M$ and $\mathbf{0}_F$ is the zero element of the vector space $F$.
