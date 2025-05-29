```
solve_model(
    file::String,
    model_type::Type,
    optimizer::Any,
    build_method::Function;
    kwargs...)::Dict{String,<:Any}
```

Instantiates and solves the modeling object from input file with file path `file`. Here, `model_type` is the model formulation type (e.g., NCWaterModel), `optimizer` is the optimization solver used to solve the problem (e.g., Gurobi.Optimizer), and `build_method` is the function used for building the problem specification being considered (e.g., build*mn*owf). Returns a dictionary of optimization results.
