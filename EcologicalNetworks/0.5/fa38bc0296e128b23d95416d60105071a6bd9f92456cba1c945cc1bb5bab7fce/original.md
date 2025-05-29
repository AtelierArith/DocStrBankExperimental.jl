```
sample(N::T, n::Int64) where {T<:AbstractBipartiteNetwork}
```

Same thing as `sample` but with a single species number, to return a bipartite network of equal richness on both sides. This is not a very good way to sample a bipartite network.
