```
centrality_harmonic(N::UnipartiteNetwork; nmax::Int64=20)
```

The function calls `shortest_path` internally – the `nmax` argument is the maximal path length that will be tried.
