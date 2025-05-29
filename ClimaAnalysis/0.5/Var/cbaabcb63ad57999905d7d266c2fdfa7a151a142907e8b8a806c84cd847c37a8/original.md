```
global_rmse(sim::OutputVar, obs::OutputVar; mask = nothing)
```

Return the global root mean squared error (RMSE) of `data` in `sim` and `obs` over longitude and latitude.

This function is currently implemented for `OutputVar`s with only the dimensions longitude and latitude. Units must be supplied for data and dimensions in `sim` and `obs`. The units for longitude and latitude should be degrees. Resampling is done automatically by resampling `obs` on `sim`.

The parameter `mask` is a function that masks a `OutputVar`. See [`apply_landmask`](@ref) and [`apply_oceanmask`](@ref).

See also [`squared_error`](@ref), [`global_mse`](@ref), [`bias`](@ref), [`global_bias`](@ref).
