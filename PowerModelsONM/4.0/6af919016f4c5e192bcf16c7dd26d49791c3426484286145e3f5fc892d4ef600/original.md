```
solve_block_mld(
    data::Dict{String,<:Any},
    model_type::Type,
    solver;
    kwargs...
)::Dict{String,Any}
```

Solves a multiconductor optimal switching (mixed-integer) problem using `model_type` and `solver`

Calls back to PowerModelsDistribution.solve*mc*model, and therefore will accept any valid `kwargs` for that function. See PowerModelsDistribution [documentation](https://lanl-ansi.github.io/PowerModelsDistribution.jl/latest) for more details.
