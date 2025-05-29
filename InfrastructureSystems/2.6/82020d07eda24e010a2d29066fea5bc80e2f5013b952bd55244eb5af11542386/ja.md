```julia
get_initial_input(
    curve::Union{InfrastructureSystems.AverageRateCurve, InfrastructureSystems.IncrementalCurve}
) -> Union{Nothing, Float64}

```

この`ValueCurve`の`initial_input`フィールドを取得します（`InputOutputCurve`には定義されていません）。
