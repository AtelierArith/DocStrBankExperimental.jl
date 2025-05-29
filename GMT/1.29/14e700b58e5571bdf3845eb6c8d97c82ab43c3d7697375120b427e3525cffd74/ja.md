```
trisurf(G, G2=nothing; bottom=false, downsample=0, isbase=false, ratio=0.01,
        thickness=0.0, wall_only=false, top_only=false, geog=false, kw...)
```

シーケンス $D = grid2tri(...)$ の短縮形で、その後に $viz(D)$ が続きます。詳細については $grid2tri$ のドキュメントを参照してください。
