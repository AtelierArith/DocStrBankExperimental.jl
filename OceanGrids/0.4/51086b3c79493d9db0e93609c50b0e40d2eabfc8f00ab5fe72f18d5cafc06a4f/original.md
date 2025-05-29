```
interpolationmatrix(g, lats, lons, depths)
interpolationmatrix(g, obs)
```

Returns the sparse matrix `M` such that `M*x` is the model vector `x` interpolated onto the provided locations in the obs table.

Technically, this requires a linear interpolation, in the sense that `interpolation(x) = M * x` for some `M`, which seems to require a nearest neighbor interpolation. If AIBECS will solely rely on this nearest neighbour interpolation, then it might be a good idea to replace Interpolations.jl with NearestNeighbors.jl. Also, the few observations that lie in model land (instead of water) are discarded.

In the future, a more generic approach will use an sparse-aware AD for any type of interpolation, and use an interpolation that somehow does not discard observations made at locations not inside an ocean grid cell.
