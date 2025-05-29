```
StraightLineHomotopy(G::System, F::System; gamma = 1.0)
StraightLineHomotopy(G::AbstractSystem, F::AbstractSystem; gamma = 1.0)
```

Constructs the straight line homotopy $H(x, t) = γ t G(x) + (1-t) F(x)$ where $γ$ is `gamma`.
