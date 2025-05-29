```
parse_events!(
    args::Dict{String,<:Any};
    validate::Bool=true,
    apply::Bool=true
)::Dict{String,Any}
```

Parses events file in-place using [`parse_events`](@ref parse_events), for use inside of [`entrypoint`](@ref entrypoint).

If `apply`, will apply the events to the multinetwork data structure.

## Validation

If `validate=true` (default), the parsed data structure will be validated against the latest [Events Schema](@ref Events-Schema).
