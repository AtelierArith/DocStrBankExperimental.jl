```
sample(N::T, n::Tuple{Int64,Int64}) where {T<:AbstractBipartiteNetwork}
```

Samples a sub-network from a bipartite network. `n` is the size of the network to return, *i.e.* number of top and bottom species. This functions makes *no* attempt to ensure that the network is not degenerate, or even has a single interaction.

This is the recommended way to sample a bipartite network.
