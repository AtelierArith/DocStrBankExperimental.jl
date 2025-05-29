```
function transform_pmitd_solution_to_eng!(
    result::Dict{String,<:Any},
    pmitd_data::Dict{String,<:Any}
)
```

Transforms the PMITD solution from MATH to ENG model. This transformation facilitates the conversion in "pmitd" of buses numbers to buses names according to the ENG model. Ex: (100002, 9, 6) -> (100002, voltage*source.3bus*unbal*nogen*mn_2.source, 6)
