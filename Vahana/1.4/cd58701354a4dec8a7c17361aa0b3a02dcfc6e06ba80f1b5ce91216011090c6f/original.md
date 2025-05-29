```
random_pos([rng], sim, raster::Symbol)
```

Return a CartesianIndex with random position coordinates.

The returned index is sampled from the rasters indizies where each index has the same probability.

See also [`random_pos(sim, raster, weights)`](@ref) and [`random_cell`](@ref)
