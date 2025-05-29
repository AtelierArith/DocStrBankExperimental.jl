```
get_channel(grid::SpmGrid, name::AbstractString,
    x_index::GridRange=:, y_index::GridRange=:, channel_index::GridRange=:;
    bwd::Bool=false)::SubArray{Float64}
```

Returns the data for the channel `name` at the point(s) specified by `x_index`, `y_index` The channel data can be indexed by `channel_index`. If `bwd` is `true`, the bwd channel is returned if it exists. If `view` is `true` (default), then a view(@ref Base.view) is returned , otherwise a copy.
