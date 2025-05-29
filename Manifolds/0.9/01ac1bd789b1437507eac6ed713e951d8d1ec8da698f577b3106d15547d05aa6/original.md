```
project(B::VectorBundle, p)
```

Project the point `p` from the ambient space of the vector bundle `B` over manifold `B.fiber` (denoted $\mathcal M$) to the vector bundle.

Notation:

  * The point $p = (x_p, V_p)$ where $x_p$ belongs to the ambient space of $\mathcal M$ and $V_p$ belongs to the ambient space of the fiber $F=π^{-1}(\{x_p\})$ of the vector bundle $B$ where $π$ is the canonical projection of that vector bundle $B$.

The projection is calculated by projecting the point $x_p$ to the manifold $\mathcal M$ and then projecting the vector $V_p$ to the tangent space $T_{x_p}\mathcal M$.
