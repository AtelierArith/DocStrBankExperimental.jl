```
calc_merit_scaling(d::Design, dist_max::Integer; kwargs...)
calc_merit_scaling(d::Design, dist_range::Vector{Int}; kwargs...)
```

Returns the scaling data as a [`MeritScaling`](@ref) object for the merit of the design `d`, for a circuit with `vertical_dist` and `horizontal_dist` parameters, as a function of these distances.

# Arguments

  * `d::Design`: Design for which the merit scaling is calculated.
  * `dist_max::Int`: Maximum distance for which the merit scaling is calculated.
  * `dist_range::Vector{Int}`: Distances for which the merit scaling is calculated.

# Keyword arguments

  * `warning::Bool = true`: Whether to print a warning if the noise model is not depolarising.
  * `diagnostics::Bool = true`: Whether to print diagnostic information.
  * `save_data::Bool = false`: Whether to save the merit scaling data.
