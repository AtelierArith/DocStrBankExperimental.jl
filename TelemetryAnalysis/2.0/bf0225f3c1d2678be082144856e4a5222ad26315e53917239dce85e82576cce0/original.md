```
save_telemetry(tms::Vector{TelemetryPacket{T}}, prefix::String = string(T)) where T<:TelemetrySource -> Nothing
```

Save the telemetries in the vector `tms` to a file. The filename is built using `prefix` together with the timestamp of the telemetries:

```
<prefix>_<timestamp of the first telemetry>_<timestamp of the last telemetry>
```

The format of timestamp if `yyyy-mm-ddTHH-MM-SS`. If `prefix` is omitted, "T" is used.
