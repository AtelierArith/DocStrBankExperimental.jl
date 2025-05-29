```
get_cumulative_climate!(climate, period; gradient_bounds=[-0.009, -0.003], default_grad=-0.0065)
```

Calculate and update the cumulative climate data for a given period.

# Keyword arguments

  * `climate::Climate`: The climate object containing raw climate data.
  * `period::Period`: The period for which to calculate the cumulative climate data.
  * `gradient_bounds::Vector{Float64}`: Optional. The bounds within which to clamp the gradient values. Default is `[-0.009, -0.003]`.
  * `default_grad::Float64`: Optional. The default gradient value to use. Default is `-0.0065`.

# Updates

  * `climate.climate_raw_step`: The raw climate data for the given period.
  * `climate.avg_temps`: The average temperature for the given period.
  * `climate.avg_gradients`: The average gradient for the given period.
  * `climate.climate_step["prcp"]`: The cumulative precipitation for the given period.
  * `climate.climate_step["temp"]`: The cumulative temperature for the given period.
  * `climate.climate_step["gradient"]`: The cumulative gradient for the given period.
  * `climate.climate_step["avg_temp"]`: The average temperature for the given period.
  * `climate.climate_step["avg_gradient"]`: The average gradient for the given period.
  * `climate.climate_step["ref_hgt"]`: The reference height from the metadata of the raw climate data.
