```
causalzigzag(n, G = (DiGraph(n), 0); balance = metropolis_balance, prior = (_,_)->1.0, score=UniformScore(),
                    coldness = 1.0, σ = 0.0, ρ = 1.0, naive=false,
                    κ = min(n - 1, 10), iterations=10, verbose=false, save=true)
```

Run the causal zigzag algorithm starting in a cpdag `(G, t)` with `t` oriented or unoriented edges, the balance function `balance ∈ {metropolis_balance, barker_balance, sqrt}`, `score` function (see `ges` algorithm) coldness parameter for iterations. `σ = 1.0, ρ = 0.0` gives purely diffusive behaviour, `σ = 0.0, ρ = 1.0` gives Zig-Zag behaviour.

Returns a vector of tuples with information, each containing a graph, spent time, current direction, number of edges and the score.
