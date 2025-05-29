```
get_device_capabilities(capabilities_file=nothing)
```

Generates a `DeviceCapabilities` struct from either an explicitly provided path to a capabilities JSON file or using the default JSON provided in "lib/BloqadeSchema/config/capabilities-qpu1-mock.json".

By default, the units for capabilities JSON file are specified by the  "lib/BloqadeSchema/config/capabilities-qpu1-mock-units.json" file this function gives a `DeviceCapabilities` struct with *non-SI base* (e.g. μm, μs) units.

See also [`get_device_capabilities_SI`](@ref)

```jldoctest;
julia> get_device_capabilities()
BloqadeSchema.DeviceCapabilities(BloqadeSchema.TaskCapabilities(1, 1000), BloqadeSchema.LatticeCapabilities(BloqadeSchema.LatticeAreaCapabilities(75.0, 76.0), BloqadeSchema.LatticeGeometryCapabilities(4.0, 4.0, 0.1, 256), 256), BloqadeSchema.RydbergCapabilities(5.42e6, BloqadeSchema.RydbergGlobalCapabilities(0.0, 15.8, 0.0004, 250.0, -125.0, 125.0, 2.0e-7, 2500.0, -99.0, 99.0, 5.0e-7, 0.0, 4.0, 0.001, 0.05), nothing))
```
