```
pagerank(g::ADiGraph, α=0.85, n=100, ϵ = 1.0e-6)
```

Calculates the [PageRank](https://en.wikipedia.org/wiki/PageRank) of the graph `g`. Can optionally specify a different damping factor (`α`), number of iterations (`n`), and convergence threshold (`ϵ`). If convergence is not reached within `n` iterations, an error will be returned.
