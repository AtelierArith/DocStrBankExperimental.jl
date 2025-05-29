```
parse_events(
    events_file::String;
    validate::Bool=true
)::Vector{Dict{String,Any}}
```

Parses an events file into a raw events data structure

## Validation

If `validate=true` (default), the parsed data structure will be validated against the latest [Events Schema](@ref Events-Schema).
