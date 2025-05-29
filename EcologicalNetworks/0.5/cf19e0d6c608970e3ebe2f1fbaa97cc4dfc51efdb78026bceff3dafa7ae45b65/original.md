```
nodiagonal(N::AbstractBipartiteNetwork)
```

Returns a *copy* of the network (because the diagonal of a bipartite network is never a meaningful notion). This function is clearly useless, but allows to write general code for all networks types when a step requires removing the diagonal.
