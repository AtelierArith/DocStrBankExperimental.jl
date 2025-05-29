```
squared_error(sim::OutputVar, obs::OutputVar; mask = nothing)
```

Return a `OutputVar` whose data is the squared error (`(sim.data - obs.data)^2`) and compute the global mean squared error (MSE) and global root mean squared error (RMSE) of `data` in `sim` and `obs` over longitude and latitude. The result is stored in `var.attributes["mse"]` and `var.attributes["rmse"]`.

This function is currently implemented for `OutputVar`s with only the dimensions longitude and latitude. Units must be supplied for data and dimensions in `sim` and `obs`. The units for longitude and latitude should be degrees. Resampling is done automatically by resampling `obs` on `sim`. Attributes in `sim` and `obs` will be thrown away. The long name and short name of the returned `OutputVar` will be updated to reflect that a squared error is computed.

The parameter `mask` is a function that masks a `OutputVar`. See [`apply_landmask`](@ref) and [`apply_oceanmask`](@ref).

See also [`global_mse`](@ref), [`global_rmse`](@ref), [`bias`](@ref), [`global_bias`](@ref).
