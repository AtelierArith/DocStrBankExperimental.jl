```
init_telemetry_source([::Type{T}, vargs...; kwargs...]) where T<:TelemetrySource -> Union{T, Nothing}
```

Initialize the telemetry source `T`. If all arguments and keywords are omitted, the function selects the source interactively.

The arguments `vargs...` and keywords `kwargs...` to initialize the source depends on the source type.

This function returns an object of type `T` if the initialization was successful or `nothing` otherwise.

!!! note
    If the source is correctly initialized, it is select as the default source.

