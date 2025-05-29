```
get_telemetry(source::T, start_time::DateTime, end_time::DateTime) where T<:TelemetrySource -> Vector{TelemetryPackets{T}}
```

Get the telemetry data using the `source` between `start_time` and `end_time`.

```
get_telemetry(::Type{T}, start_time::DateTime, interval) where T<:TelemetrySource -> Vector{TelemetryPackets{T}}
```

Get the telemetry data using the `source` from `start_time` up to `start_time + interval`. `interval` must be a number with a time unit. The following units are exported:

  * `s` for seconds;
  * `m` for minutes;
  * `h` for hours; and
  * `d` for day.

If `source` is omitted, the default telemetry source is used. For more information, see [`set_default_telemetry_source!`](@ref).

Some sources may also implement the simplified version of this function:

```
get_telemetry(::Type{T}) where T<:TelemetrySource -> Vector{TelemetryPackets{T}}
```

where all the available telemetry will be fetched.

!!! note
    The telemetry obtained from this function is selected as the default telemetry packet.


# Returns

  * `Vector{TelemetryPacket{T}}`: A vector with the telemetry packets.
