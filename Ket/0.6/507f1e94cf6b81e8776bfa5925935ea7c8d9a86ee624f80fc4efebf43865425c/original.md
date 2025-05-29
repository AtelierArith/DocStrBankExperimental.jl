```
local_bound(G::Array{T,N}; correlation = N < 4, marg = true)
```

Computes the local bound of a multipartite Bell functional `G` given as an `N`-dimensional array. If `correlation` is `false`, `G` is assumed to be written in probability notation. If `correlation` is `true`, `G` is assumed to be written in correlation notation, with or without marginals depending on `marg`.

Reference: Araújo, Hirsch, Quintino, [arXiv:2005.13418](https://arxiv.org/abs/2005.13418)
