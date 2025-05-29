```
dilate!(p, A; limit = nothing)
```

Perform a single pass of dilation on `Parcel` `p`, guided by adjacency matrix `A`; optionally specify a `limit::Int` on the number of new vertices that can be added.
