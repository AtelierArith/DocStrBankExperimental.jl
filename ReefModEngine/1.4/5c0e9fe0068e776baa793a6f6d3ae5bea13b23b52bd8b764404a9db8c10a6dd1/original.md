```
set_outplant_deployment!(
    name::String,
    reefset::String,
    max_effort::Int64,
    first_year::Int64,
    last_year::Int64,
    year_step::Int64,
    area_km2::Vector{Float64},
)::Nothing
```

Set outplanting deployments across a range of years, automatically determining the coral deployment density to maintain the set grid size.
