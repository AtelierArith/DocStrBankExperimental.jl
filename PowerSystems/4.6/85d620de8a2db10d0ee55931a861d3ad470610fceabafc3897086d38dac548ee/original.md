```julia
from_json(
    io::Union{IO, String},
    ::Type{PowerSystems.System};
    runchecks,
    assign_new_uuids,
    kwargs...
) -> PowerSystems.System

```

If assign*new*uuids = true, generate new UUIDs for the system and all components.

Warning: time series data is not restored by this method. If that is needed, use the normal process to construct the system from a serialized JSON file instead, such as with `System("sys.json")`.
