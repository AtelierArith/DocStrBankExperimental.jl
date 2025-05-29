```
nonlinear_model(
    model::Model;
    force::Bool = false,
)::Union{MOI.Nonlinear.Model,Nothing}
```

If `model` has nonlinear components, return a [`MOI.Nonlinear.Model`](@ref), otherwise return `nothing`.

If `force`, always return a [`MOI.Nonlinear.Model`](@ref), and if one does not exist for the model, create an empty one.
