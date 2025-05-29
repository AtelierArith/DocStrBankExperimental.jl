```
set_outplant_deployment!(name::String, reefset::String, n_corals::Int64, max_effort::Int64, first_year::Int64, last_year::Int64, year_step::Int64, area_km2::Vector{Float64}, density::Float64)::Nothing
```

Set outplanting deployments across a range of years.

# Arguments

  * `name` : Name to assign intervention event
  * `reefset` : Name of pre-defined list of reefs to intervene on
  * `n_corals` : Number of corals to outplant for a given year
  * `max_effort` : Total number of corals to outplant
  * `first_year` : First year to start interventions
  * `last_year` : Final year of interventions
  * `year_step` : Frequency of intervention (1 = every year, 2 = every second year, etc)
  * `area_km2` : Intervention area [km²]
  * `density` : Stocking density of intervention [corals / m²]
