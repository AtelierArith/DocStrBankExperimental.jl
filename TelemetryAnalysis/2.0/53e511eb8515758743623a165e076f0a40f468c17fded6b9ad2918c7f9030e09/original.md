```
struct TelemetryDatabase{F1 <: Function, F2 <: Function}
```

Defines a telemetry database.

# Fields

  * `label::String`: Database label.
  * `get_telemetry_timestamp::F1`: Function to get the timestamp of a telemetry packet.
  * `unpack_telemetry::F2`: Function to unpack the telemetry packet, obtaining the data that   will be passed to the transfer functions.
  * `variables::OrderedDict{Symbol, TelemetryVariableDescription}`: Telemetry variables.
