```
solve_model(
    data::Dict{String,<:Any},
    model_type::Type,
    optimizer::Any,
    build_method::Function;
    ref_extensions::Vector{<:Function} = Vector{Function}([]),
    solution_processors::Vector{<:Function} = Vector{Function}([]),
    relax_integrality::Bool = false,
    multinetwork::Bool = false,
    kwargs...)::Dict{String, <:Any}
```

Instantiates and solves the modeling object from data dictionary `data`. Here, `model_type` is the model formulation type (e.g., NCWaterModel), `optimizer` is the optimization solver used to solve the problem (e.g., Gurobi.Optimizer), and `build_method` is the function used for building the problem specification being considered (e.g., build*mn*owf). Moreover, `ref_extensions` is a vector of functions that modify `ref`, `solution_processors` is a vector of functions that post-process model solutions, `relax_integrality` is a Boolean indicating if the model solved should be continuously relaxed, and `multinetwork` is a Boolean indicating whether or not the model being solved is a multinetwork model. Returns a dictionary of optimization results.
