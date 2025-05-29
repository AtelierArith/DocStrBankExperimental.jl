```
struct TelemetryPacket{T <: TelemetrySource}
```

Telemetry packet obtained from the source `T`.

# Fields

  * `timestamp::DateTime`: The timestamp of the telemetry packet.
  * `data::Vector{UInt8}`: The telemetry data encapsulated in a vector of `UInt8`.
  * `metadata::Dict{String, Any}`: A dictionary to hold meta data about the telemetry packet.
