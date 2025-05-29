```julia
GetIndexPath(start::Vector{Int64}, ending::Vector{Int64} ; exclusive::Bool=true) --> Vector{Vector{Int64}}
```

Returns a path in index-space of a discretized lattice which joins the two sets of indices `start` and `ending`.  If the input `exclusive` is set to `true`, the returned path will NOT contain the `ending` point itself. Works in any dimensions.
