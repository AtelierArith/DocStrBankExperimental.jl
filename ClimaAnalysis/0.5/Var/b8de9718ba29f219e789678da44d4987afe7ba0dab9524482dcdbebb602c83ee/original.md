```
bias(sim::OutputVar, obs::OutputVar; mask = nothing)
```

Return a `OutputVar` whose data is the bias (`sim.data - obs.data`) and compute the global bias of `data` in `sim` and `obs` over longitude and latitude. The result is stored in `var.attributes["global_bias"]`.

This function is currently implemented for `OutputVar`s with only the dimensions longitude and latitude. Units must be supplied for data and dimensions in `sim` and `obs`. The units for longitude and latitude should be degrees. Resampling is done automatically by resampling `obs` on `sim`. Attributes in `sim` and `obs` will be thrown away. The long name and short name of the returned `OutputVar` will be updated to reflect that a bias is computed.

The parameter `mask` is a function that masks a `OutputVar`. See [`apply_landmask`](@ref) and [`apply_oceanmask`](@ref).

See also [`global_bias`](@ref), [`squared_error`](@ref), [`global_mse`](@ref), [`global_rmse`](@ref).
