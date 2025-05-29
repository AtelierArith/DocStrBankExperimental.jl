```
parse_events(
    raw_events::Vector{<:Dict{String,<:Any}},
    mn_data::Dict{String,<:Any}
)::Dict{String,Any}
```

Converts `raw_events`, e.g. loaded from JSON, and therefore in the format Vector{Dict}, to an internal data structure that closely matches the multinetwork data structure for easy merging (applying) to the multinetwork data structure.

Will attempt to find the correct subnetwork from the specified timestep by using "mn_lookup" in the multinetwork data structure.

## Switch events

Will find the correct switch id from a `source_id`, i.e., the asset*type.name from the source file, which for switches will be `line.name`, and create a data structure containing the properties defined in `event*data` under the native ENGINEERING switch id.

## Fault events

Will attempt to find the appropriate switches that need to be OPEN to isolate a fault, and disable them, i.e., set `dispatchable=false`, until the end of the `duration` of the fault, which is specified in milliseconds.

It will re-enable the switches, i.e., set `dispatchable=true` after the fault has ended, if the next timestep exists, but will not automatically set the switches to CLOSED again; this is a decision for the algorithm [`optimize_switches`](@ref optimize_switches) to make.
