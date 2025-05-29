```
process_telemetry_packets([tmpackets::Vector{TelemetryPacket{T}}]; database::TelemetryDatabase, kwargs...) where T <: TelemetrySource -> DateFrame
```

Process the telemetry packets `tmpackets` using the `database`, returning the processed values of **all** registered telemetries. If `tmpackets` are not passed, the default telemetry packets will be used.

```
process_telemetry_packets([tmpackets::Vector{TelemetryPacket{T}},] telemetries::AbstractVector; database::TelemetryDatabase, kwargs...) where T <: TelemetrySource -> DataFrame
```

Process the telemetry packets `tmpackets` using the `database`. The elements in `telemetries` can be a `Symbol` with the telemetry label or a `Pair{Symbol, Symbol}`. In the former, the default view will be used. In the latter, the variable view will be as specified by the second symbol in the pair.  For more information, see the section below.

If `tmpackets` are not passed, the default telemetry packets will be used.

```
process_telemetry_packets([tmpackets::Vector{TelemetryPacket{T}},] telemetries::Vector{Pair{Symbol, Symbol}}; database::TelemetryDatabase, kwargs...) where T <: TelemetrySource -> DataFrame
```

Process the telemetry packets `tmpackets` using the `database`. The output variables are indicated in `telemetries`. It must be a vector of pairs indicating the telemetry and how the value is written to the output. For example, `:C001 => :raw` adds the raw value of telemetry `C001`, whereas `:C001 => :processed` adds the processed value of the same variable.

The acceptable values for the output format are:

  * `:byte_array`: `Vector{UInt8}` with the telemetry byte array.
  * `:byte_array_bin`: String with the raw value represented in binary.
  * `:byte_array_hex`: String with the raw value represented in hexadecimal.
  * `:processed`: Processed value obtained from the transfer function.
  * `:raw`: Telemetry raw value.

If `tmpackets` are not passed, the default telemetry packets will be used.

!!! info
    If the keyword argument `database` is not passed, the default database is used.


# Keywords

  * `show_progress::Bool`: If `true`, a progress bar is shown while processing the   telemetries. (**Default** = `true`)

# Return

  * `DataFrame`: A `DataFrame` in which the columns are the selected values. The column names   are the variable labels.
