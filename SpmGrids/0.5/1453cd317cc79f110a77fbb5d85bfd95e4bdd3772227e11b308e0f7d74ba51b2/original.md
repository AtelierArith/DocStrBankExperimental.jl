```
channel_names(grid::SpmGrid, skip_bwd=true)::Array{String}
```

Returns all channel names in `grid`. If `skip_bwd` is `true`, then the channel names for the bwds direction are not returned.
