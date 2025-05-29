```julia
test_differentiation(
    backend::ADTypes.AbstractADType,
    args...;
    kwargs...
) -> Union{Nothing, DataFrames.DataFrame}

```

単一のバックエンドのショートカットです。
