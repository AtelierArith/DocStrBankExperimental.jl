```
overlap(N::T; dims=dims::Union{Nothing,Integer}=nothing) where {T <: BipartiteNetwork}
```

Returns the overlap graph for a bipartite network. The `dims` keyword argument can be `1` (default; overlap between top-level species) or `2` (overlap between bottom-level species). See the documentation for `?overlap` for the output format.
