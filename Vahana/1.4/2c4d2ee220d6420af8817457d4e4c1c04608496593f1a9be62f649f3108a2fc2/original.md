```
random_pos([rng], sim, raster::Symbol, weights::Matrix)
```

Return a CartesianIndex with random position coordinates, weighted by a probability matrix `weights`.

The likelihood of selecting a particular cell/index is proportional to its corresponding value in the `weights` matrix.

See also [`random_pos(sim, raster)`](@ref) and [`random_cell`](@ref)
