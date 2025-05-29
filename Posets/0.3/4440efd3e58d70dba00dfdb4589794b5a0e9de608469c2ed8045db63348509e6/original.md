```
cover_digraph(p::Poset{T}) where {T}
```

Create a directed graph with the same vertices a `p` in which there is  an edge from `v` to `w` exactly when `v` is covered by `w` in `p`.
