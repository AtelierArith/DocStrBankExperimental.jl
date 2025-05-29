```
StraightLineHomotopy(G::System, F::System; gamma = 1.0)
StraightLineHomotopy(G::AbstractSystem, F::AbstractSystem; gamma = 1.0)
```

直線ホモトピー $H(x, t) = γ t G(x) + (1-t) F(x)$ を構築します。ここで、$γ$ は `gamma` です。
