```
project(B::VectorBundle, p, X)
```

Project the element `X` of the ambient space of the tangent space $T_p B$ to the tangent space $T_p B$.

Notation:

  * The point $p = (x_p, V_p)$ where $x_p ∈ \mathcal M$ and $V_p$ belongs to the fiber $F=π^{-1}(\{x_p\})$ of the vector bundle $B$ where $π$ is the canonical projection of that vector bundle $B$.
  * The vector $x = (V_{X,M}, V_{X,F})$ where $x_p$ belongs to the ambient space of $T_{x_p}\mathcal M$ and $V_{X,F}$ belongs to the ambient space of the fiber $F=π^{-1}(\{x_p\})$ of the vector bundle $B$ where $π$ is the canonical projection of that vector bundle $B$.

The projection is calculated by projecting $V_{X,M}$ to tangent space $T_{x_p}\mathcal M$ and then projecting the vector $V_{X,F}$ to the fiber $F$.
