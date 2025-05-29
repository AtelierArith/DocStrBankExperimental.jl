```
raster_pullback!(
    ds_dout, args...;
    [points, rotation, translation, background, out_weight, point_weight]
)
```

Pullback for [`raster`](@ref) / [`raster!`](@ref).

Take as input `ds_dout` the sensitivity of some quantity (`s` for "scalar") to the *output* `out` of the function `out = raster(grid_size, args...)` (or `out = raster!(out, args...)`), as well as the exact same arguments `args` that were passed to `raster`/`raster!`, and return the sensitivities of `s` to the *inputs* `args` of the function `raster`/`raster!`.

Optionally, pre-allocated output arrays for each input sensitivity can be specified as keyword arguments with the name of the original argument to `raster` as key, and a nd-array as value, where the n-th dimension is the batch dimension. For example to provide a pre-allocated array for the sensitivity of `s` to the `translation` argument of `raster`, do: `sensitivities = raster_pullback!(ds_dout, args...; translation = [zeros(2) for _ in 1:8])` for 2-dimensional points and a batch size of 8. See also [Raster a single point cloud to a batch of poses](@ref)
