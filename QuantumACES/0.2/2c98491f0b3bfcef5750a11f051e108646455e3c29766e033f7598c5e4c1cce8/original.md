```
EnsembleScaling
```

Ensemble scaling data for an experimental design for a circuit with vertical and horizontal distance parameters under a random noise model.

# Fields

  * `d::Design`: Design for which the scaling data is calculated.
  * `dist_range::Vector{Int}`: Circuit distances.
  * `merits::Vector{Merit}`: Merits of the design for each distance.
  * `merit_ensemble::Vector{Vector{Merit}}`: Merits of the design across random noise models for each distance.
  * `seeds::Vector{UInt64}`: Seeds for the random noise parameters.
  * `calculation_times::Matrix{Float64}`: The time to generate the design, calculate the depolarising merit, and calculate the merit ensemble, for each distance.
  * `overall_time::Float64`: The overall time taken to calculate the merit ensemble scaling data.
