```
sample(N::T, n::Tuple{Int64}) where {T<:AbstractUnipartiteNetwork}
```

Same as `sample`, but work when called with `(n,)` instead of a species number. This is an accepted way to sample a unipartite network.
