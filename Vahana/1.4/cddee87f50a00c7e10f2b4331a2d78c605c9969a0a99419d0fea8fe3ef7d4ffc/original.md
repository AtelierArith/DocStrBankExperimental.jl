```
random_cell([rng], sim, raster::Symbol, weights::Array)
```

Return a random cell id of the raster `raster` from the simulation `sim`. The likelihood of selecting a particular cell is proportional to its corresponding value in the `weights` matrix.

See also [`random_cell(sim, raster)`](@ref) and [`random_pos`](@ref)
