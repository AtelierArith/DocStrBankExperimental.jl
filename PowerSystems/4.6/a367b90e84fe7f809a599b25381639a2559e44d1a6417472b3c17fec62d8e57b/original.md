```julia
ACBus(
    number,
    name,
    bustype::String,
    angle,
    voltage,
    voltage_limits,
    base_voltage,
    area,
    load_zone;
    ext
) -> PowerSystems.ACBus

```

Allows construction with bus type specified as a string for legacy code.
