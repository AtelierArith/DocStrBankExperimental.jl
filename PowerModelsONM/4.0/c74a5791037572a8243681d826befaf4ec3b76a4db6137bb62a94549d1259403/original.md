```
solve_onm_model(
    data::Union{Dict{String,<:Any}, String},
    model_type::Type,
    solver::Any,
    model_builder::Function;
    solution_processors::Vector{Function}=Function[],
    eng2math_passthrough::Dict{String,Vector{String}}=Dict{String,Vector{String}}(),
    ref_extensions::Vector{Function}=Function[],
    multinetwork::Bool=false,
    global_keys::Set{String}=Set{String}(),
    kwargs...
)::Dict{String,Any}
```

Custom version of `PowerModelsDistribution.solve_mc_model` that automatically includes the solution processors, ref extensions and eng2math_passthroughs required for ONM problems.
