```
create_edge!(from::AbstractVertex, to::AbstractVertex; [pos], [strategy])
```

Create and edge from `from` to `to` at index `pos` in [`inputs(to)`](@ref).

Sizes will be adjusted based on given `strategy`.
