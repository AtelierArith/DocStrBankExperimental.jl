```
centrality_katz(N::Unipartite; a::Float64=0.1, k::Int64=5)
```

This measure can work on different path length (`k`), and give a different weight to every subsequent connection (`a`). `k` must be at least 1 (only immediate neighbors are considered). `a` (being a weight), must be positive.

> Katz, L., 1953. A new status index derived from sociometric analysis. Psychometrika 18, 39–43. doi:10.1007/bf02289026

