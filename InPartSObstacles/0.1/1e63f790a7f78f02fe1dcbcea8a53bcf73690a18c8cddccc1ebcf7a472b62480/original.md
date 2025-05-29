```
ngonwalls(n, walltype = InfiniteWall{2, Absorbing}; kwargs...)
```

Construct a regular polygonal domain with `n` corners and `walltype` walls. The size can be provided as keyword arguments by giving a the radius `r` of the circumcircle `r` or the area `A` (of the polygon) plus an additional `wallsize=0.05` margin.
