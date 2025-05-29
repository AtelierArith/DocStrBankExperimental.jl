```julia
struct InvalidTree
```

Information about an invalid (sub)tree, using positions relative to the starting node.

1. When `left < right`, this tree was *turning*.
2. When `left == right`, this is a *divergent* node.
3. `left == 1 && right == 0` is used as a sentinel value for reaching maximum depth without

encountering any invalid trees (see [`REACHED_MAX_DEPTH`](@ref). All other `left > right` values are disallowed.

# Fields

  * `left::Int64`
  * `right::Int64`
