```
parse_inverters(
    inverter_file::String;
    validate::Bool=true
)::Dict{String,Any}
```

Parses an inverters JSON file, used in [`run_stability_analysis!`](@ref run_stability_analysis!)

## Validation

If `validate=true` (default), the parsed data structure will be validated against the latest [Inverters Schema](@ref Inverters-Schema).
