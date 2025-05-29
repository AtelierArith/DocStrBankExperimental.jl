```
sample(N::T, n::Tuple{Int64}) where {T<:AbstractBipartiteNetwork}
```

Same as `sample` but with a single species number given as `(n,)`, to return a bipartite network of equal richness on both sides. This is not a very good way to sample a bipartite network.
