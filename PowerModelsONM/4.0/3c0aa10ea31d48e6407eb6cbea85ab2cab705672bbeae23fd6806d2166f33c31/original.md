```
parse_settings(
    settings_file::String;
    validate::Bool=true
    correct::Bool=true
)::Dict{String,Any}
```

Parses network settings JSON file.

## Validation

If `validate=true` (default), the parsed data structure will be validated against the latest [Settings Schema](@ref Settings-Schema).
