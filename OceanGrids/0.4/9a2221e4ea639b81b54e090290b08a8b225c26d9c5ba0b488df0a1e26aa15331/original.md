```
iswet(g, lat, lon, depth)
iswet(g, lats, lons, depths)
iswet(g, obs)
```

Returns a `BitArray` of the provided locations that are "in" a wet box of `g`.

Technically, this uses a nearest neighbour interpolation algorithm, so the bounding boxes will not work perfectly. If AIBECS will solely rely on this nearest neighbour interpolation, then it might be a good idea to replace Interpolations.jl with NearestNeighbors.jl.
