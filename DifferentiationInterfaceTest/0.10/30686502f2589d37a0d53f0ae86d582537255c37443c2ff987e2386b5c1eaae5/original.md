```julia
test_differentiation(
    backend::ADTypes.AbstractADType,
    args...;
    kwargs...
) -> Union{Nothing, DataFrames.DataFrame}

```

Shortcut for a single backend.
