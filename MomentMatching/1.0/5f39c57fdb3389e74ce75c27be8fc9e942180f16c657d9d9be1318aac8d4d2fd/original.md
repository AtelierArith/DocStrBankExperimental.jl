```julia
ftypemom(
    mode::MomentMatching.EstimationMode,
    modelname::String
) -> String

```

Given the model name prepares a string corresponding to the default moments to be matched in [`estimation`](@ref).

Defaults to empty string when no mode-specific method is defined.
