```
automorphism_group_order(L::AbstractLat; depth::Int = -1, bacher_depth::Int = 0) -> Int
```

Given a definite lattice `L`, return the order of the automorphism group of `L`.

Setting the parameters `depth` and `bacher_depth` to a positive value may improve performance. If set to `-1` (default), the used value of `depth` is chosen heuristically depending on the rank of `L`. By default, `bacher_depth` is set to `0`.
