```
parse_events(
    events_file::String,
    mn_data::Dict{String,<:Any};
    validate::Bool=true
)::Dict{String,Any}
```

Parses raw events from `events_file` and passes it to [`parse_events`](@ref parse_events) to convert to the native data type.

## Validation

If `validate=true` (default), the parsed data structure will be validated against the latest [Events Schema](@ref Events-Schema).
