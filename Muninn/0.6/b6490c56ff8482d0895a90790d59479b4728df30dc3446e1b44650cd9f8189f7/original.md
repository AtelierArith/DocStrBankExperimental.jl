```
MB_timestep!(model::Model, glacier::G, step::F, t; batch_id::Union{Nothing, I} = nothing) where {I <: Integer, F <: AbstractFloat, G <: AbstractGlacier}
```

Simulates a mass balance timestep for a given glacier model.

# Arguments

  * `model::Model`: The glacier model containing iceflow and mass balance information.
  * `glacier::G`: The glacier object containing climate and DEM data.
  * `step::F`: The timestep duration.
  * `t`: The current time.
  * `batch_id::Union{Nothing, I}`: Optional batch identifier for simulations using Reverse Diff. Defaults to `nothing`.

# Description

This function performs the following steps:

1. Computes the period from the previous timestep to the current time.
2. Retrieves cumulative climate data for the specified period.
3. Downscales the climate dataset to a 2D grid based on the glacier's DEM.
4. Computes the mass balance for the glacier and updates the model's iceflow mass balance.

If `batch_id` is provided, the function updates the mass balance for the specified batch; otherwise, it updates the mass balance for the entire model.
