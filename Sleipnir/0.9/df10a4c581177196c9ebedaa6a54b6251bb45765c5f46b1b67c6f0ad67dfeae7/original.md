```
get_cumulative_climate(climate; gradient_bounds=[-0.009, -0.003], default_grad=-0.0065)
```

Calculate cumulative climate statistics from the given climate data.

# Keyword arguments

  * `climate::Climate`: A climate object containing temperature, precipitation, and gradient data.
  * `gradient_bounds::Vector{Float64}`: A two-element vector specifying the lower and upper bounds for the gradient values. Defaults to `[-0.009, -0.003]`.
  * `default_grad::Float64`: The default gradient value to use. Defaults to `-0.0065`.

# Returns

  * `climate_sum::Dict{String, Any}`: A dictionary containing the following keys:

      * `"temp"`: The sum of positive degree days (PDDs) from the temperature data.
      * `"prcp"`: The sum of precipitation data.
      * `"gradient"`: The sum of gradient data, clipped within the specified bounds.
      * `"avg_temp"`: The average temperature.
      * `"avg_gradient"`: The average gradient.
      * `"ref_hgt"`: The reference height from the climate metadata.

# Notes

  * The temperature data is modified to only include positive degree-day values (PDDs).
  * The gradient data is clipped within the specified bounds to ensure plausible values.
