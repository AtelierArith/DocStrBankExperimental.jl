```
pagerank(g, α=0.85, n=100, ϵ=1.0e-6)
```

Calculate the [PageRank](https://en.wikipedia.org/wiki/PageRank) of the graph `g` parameterized by damping factor `α`, number of iterations  `n`, and convergence threshold `ϵ`. Return a vector representing the centrality calculated for each node in `g`, or an error if convergence is not reached within `n` iterations.
