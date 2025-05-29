```
instantiate_model(
    data::Dict{String,<:Any},
    model_type::Type,
    build_method::Function;
    kwargs...)::AbstractWaterModel
```

Instantiates and returns a WaterModels object from input file with file path `file`. Here, `model_type` is the formulation type (e.g., NCWaterModel) and `build_method` is the function for building the problem specification being considered (e.g., build*mn*owf).
