```
sample(N::T, n::Int64) where {T<:AbstractUnipartiteNetwork}
```

Samples a sub-network from a unipartite network. `n` is the number of species to have in the sampled network. This functions makes *no* attempt to ensure that the network is not degenerate, or even has a single interaction. This is the recommended way to sample a unipartite network.
