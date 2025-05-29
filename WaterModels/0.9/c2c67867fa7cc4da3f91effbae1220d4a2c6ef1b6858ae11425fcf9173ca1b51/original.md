```
instantiate_model(
    file::String,
    model_type::Type,
    build_method::Function;
    kwargs...)::AbstractWaterModel
```

Instantiates and returns a WaterModels object from data dictionary `data`. Here, `model_type` is the formulation type (e.g., NCWaterModel) and `build_method` is the function for building the problem specification being considered (e.g., build_owf).
