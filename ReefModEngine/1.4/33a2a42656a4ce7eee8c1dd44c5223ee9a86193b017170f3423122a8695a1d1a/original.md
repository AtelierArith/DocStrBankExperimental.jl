```
deployment_area(n_corals::Int64, max_n_corals::Int64, density::Float64, target_areas::Vector{Float64})::Tuple{Float64,Float64}
```

Determine deployment area for the expected number of corals to be deployed.

# Arguments

  * `n_corals` : Number of corals,
  * `max_n_corals` : Expected maximum deployment effort (total number of corals in intervention set)
  * `density` : Stocking density per m²
  * `target_areas` : Available area at target location(s)

# Returns

Tuple

  * Percent area of deployment
  * modified stocking density [currently no modifications are made]
