```
trisurf(G, G2=nothing; bottom=false, downsample=0, isbase=false, ratio=0.01,
        thickness=0.0, wall_only=false, top_only=false, geog=false, kw...)
```

Short form for the sequence $D = grid2tri(...)$ followed by $viz(D)$. See the documentation of $grid2tri$ for more details.
