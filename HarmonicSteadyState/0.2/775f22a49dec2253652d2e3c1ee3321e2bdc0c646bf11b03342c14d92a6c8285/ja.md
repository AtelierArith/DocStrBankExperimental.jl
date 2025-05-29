```julia
get_class(
    res::HarmonicSteadyState.Result,
    branch::Int64,
    class::String
) -> Any

```

`res`の解において`class`に従って`branch`を分類するブール値の配列を返します。
