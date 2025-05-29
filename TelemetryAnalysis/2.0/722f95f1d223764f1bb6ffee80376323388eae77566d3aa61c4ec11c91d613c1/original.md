```
create_telemetry_database(label::String; kwargs...) -> TelemetryDatabase
```

Create a telemetry database with `label`.

# Keywords

  * `get_telemetry_timestamp::Function`: A function that must return the timestamp of a   telemetry packet. The API is:

    `get_telemetry_timestamp(tmpacket::TelemetryPacket)::DateTime`

    (**Default** = `_default_get_telemetry_timestamp`)
  * `unpack_telemetry::Function`: A function that must return a `AbstractVector{UInt8}` with   the telemetry frame unpacked, which will be passed to the transfer functions. If the   frame is not valid, it must return `nothing`. The function API must be:

    `unpack_telemetry(tmpacket::TelemetryPacket)::AbstractVector{UInt8}`

    (**Default** = `_default_unpack_telemetry`)
