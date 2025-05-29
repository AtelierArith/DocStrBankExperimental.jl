```
MultiSegmentWell(reservoir_cells, volumes, centers;
                N = nothing,
                name = :Well,
                perforation_cells = nothing,
                segment_models = nothing,
                segment_length = nothing,
                reference_depth = 0,
                dz = nothing,
                surface_conditions = default_surface_cond(),
                accumulator_volume = mean(volumes),
                )
```

Create well perforated in a vector of `reservoir_cells` with corresponding `volumes` and cell `centers`.

# Note

[`setup_vertical_well`](@ref) or [`setup_well`](@ref) are the recommended way of setting up wells.

# Fields

  * `type`
  * `volumes`
  * `perforations`
  * `neighborship`
  * `top`
  * `centers`
  * `surface`
  * `name`
  * `segment_models`
  * `material_thermal_conductivity`
  * `material_density`
  * `material_heat_capacity`
  * `void_fraction`
