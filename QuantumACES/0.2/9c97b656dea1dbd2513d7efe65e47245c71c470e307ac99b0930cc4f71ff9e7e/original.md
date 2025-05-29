```
calc_ensemble_scaling(d::Design, dist_max::Integer; kwargs...)
calc_ensemble_scaling(d::Design, dist_range::Vector{Int}; kwargs...)
```

Returns ensemble scaling data as a [`EnsembleScaling`](@ref) object for the merit of the design `d` over random instances of noise models, for a circuit with `vertical_dist` and `horizontal_dist` parameters, as a function of these distances.

# Arguments

  * `d::Design`: Design for which the merit scaling is calculated.
  * `dist_max::Int`: Maximum code distance for which the merit scaling is calculated.
  * `dist_range::Vector{Int}`: Code distances for which the merit scaling is calculated.

# Keyword arguments

  * `precision::Real = 2e-3`: Precision to which the figure of merit is estimated, corresponding to the target standard error of the mean.
  * `max_repetitions::Integer = 10000`: Maximum number of random instances of log-normal Pauli noise over which the figure of merit is calculated.
  * `min_repetitions::Integer = 50`: Minimum number of random instances of log-normal Pauli noise over which the figure of merit is calculated.
  * `print_repetitions::Integer = 50`: Number of random instances of log-normal Pauli noise between printing diagnostics.
  * `seed::Union{UInt64, Nothing} = nothing`: Seeds used to generate instances of log-normal Pauli noise.
  * `diagnostics::Bool = true`: Whether to print diagnostic information.
  * `save_data::Bool = false`: Whether to save the merit scaling data.
