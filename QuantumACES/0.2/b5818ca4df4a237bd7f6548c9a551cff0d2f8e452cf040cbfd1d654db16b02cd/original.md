```
MeritScaling
```

Scaling data for an experimental design for a circuit with vertical and horizontal distance parameters, conventionally under depolarising noise.

# Fields

  * `d::Design`: Design for which the scaling data is calculated.
  * `dist_range::Vector{Int}`: Circuit distances.
  * `merits::Vector{Merit}`: Merits of the design for a range of distances.
  * `calculation_times::Matrix{Float64}`: Time taken to generate the design, and calculate the merit, for each distance.
  * `overall_time::Float64`: The overall time taken to calculate the merit scaling data for depolarising noise.
