```
is_isometric(L::AbstractLat, M::AbstractLat; depth::Int = -1, bacher_depth::Int = 0) -> Bool
```

Return whether the lattices `L` and `M` are isometric.

Setting the parameters `depth` and `bacher_depth` to a positive value may improve performance. If set to `-1` (default), the used value of `depth` is chosen heuristically depending on the rank of `L`. By default, `bacher_depth` is set to `0`.
