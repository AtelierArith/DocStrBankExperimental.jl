```
sample(N::T, n::Tuple{Int64,Int64}) where {T<:AbstractUnipartiteNetwork}
```

Same as `sample` but called with `(n,n)` instead of a species number. Note that this will fail if the size requested is not square. This is not a really good way to sample a unipartite network.
