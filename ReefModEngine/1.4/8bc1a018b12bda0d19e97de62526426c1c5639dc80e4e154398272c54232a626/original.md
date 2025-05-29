```
set_outplant_deployment!(name::String, reefset::String, n_corals::Int64, year::Int64, area_km2::Vector{Float64})::Nothing
```

Set outplanting deployments for a single year, automatically determining the coral deployment density to maintain the set grid size.

# Arguments

  * `name` : Name to assign intervention event
  * `reefset` : Name of pre-defined list of reefs to intervene on
  * `n_corals` : Number of corals to outplant
  * `year` : Year to intervene
  * `area_km2` : Area to intervene [km²]
