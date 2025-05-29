```
parse_settings!(
    args::Dict{String,<:Any};
    apply::Bool=true,
    validate::Bool=true
)::Dict{String,Any}
```

Parses settings file specifed in runtime arguments in-place

Will attempt to convert deprecated runtime arguments to appropriate network settings data structure.

## Validation

If `validate=true` (default), the parsed data structure will be validated against the latest [Settings Schema](@ref Settings-Schema).
