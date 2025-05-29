```
MB_timestep(model::Model, glacier::G, step::F, t::F) where {F <: AbstractFloat, G <: AbstractGlacier}
```

Calculate the mass balance (MB) for a glacier over a given timestep.

# Keyword arguments

  * `model::Model`: The model containing mass balance parameters.
  * `glacier::G`: The glacier object containing climate and DEM data.
  * `step::F`: The timestep duration.
  * `t::F`: The current time.

# Returns

  * `MB::Matrix{F}`: The computed mass balance matrix for the given timestep.

# Details

1. Computes the period between the current time `t` and the previous step `t - step`.
2. Retrieves cumulative climate data for the specified period.
3. Downscales the climate data to a 2D grid based on the glacier's DEM.
4. Computes the mass balance using the downscaled climate data.
