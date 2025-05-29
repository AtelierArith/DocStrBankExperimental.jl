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

ONM問題に必要なソリューションプロセッサ、参照拡張、およびeng2math*passthroughを自動的に含む`PowerModelsDistribution.solve*mc_model`のカスタムバージョン。
