```
PSO(f, population, k_max; w=1, c1=1, c2=1)
PSO(logger::Logbook, f, population, k_max; w=1, c1=1, c2=1)
```

## Arguments

  * `f::Function`: Objective function to **minimise**.
  * `population::Vector{Particle}`: a list of [`Particle`](@ref) individuals.
  * `k_max::Integer`: number of iterations.

## Keywords

  * `w`: inertia weight. Optional, by default 1.
  * `c1`: cognitive coefficient (own's position). Optional, by default 1.
  * `c2`: social coefficient (others' position). Optional, by default 1.

Returns a [`Result`](@ref).
