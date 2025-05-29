```
erode!(p, neighbors; limit = nothing)
```

Perform a single pass of erosion on `Parcel` `p`, guided by adjacency list `neighbors`; optionally specify a `limit::Int` on the number of vertices that you want to remove.
