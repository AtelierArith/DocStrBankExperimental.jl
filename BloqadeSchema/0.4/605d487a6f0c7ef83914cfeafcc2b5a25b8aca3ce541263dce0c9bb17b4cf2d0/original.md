```
get_device_capabilities_SI(capabilities_file=nothing)
```

Generates a `DeviceCapabilities` struct from either an explicitly provided path to a capabilities JSON file or using the default JSON provided in "lib/BloqadeSchema/config/capabilities-qpu1-mock.json".

The values returned are in Base SI units: m, s, rad/s, etc.

```jldoctest;
julia> get_device_capabilities_SI()
BloqadeSchema.DeviceCapabilities(BloqadeSchema.TaskCapabilities(1, 1000), BloqadeSchema.LatticeCapabilities(BloqadeSchema.LatticeAreaCapabilities(7.5e-5, 7.6e-5), BloqadeSchema.LatticeGeometryCapabilities(4.0e-6, 4.0e-6, 1.0e-7, 256), 256), BloqadeSchema.RydbergCapabilities(5.42e-24, BloqadeSchema.RydbergGlobalCapabilities(0.0, 1.58e7, 400.0, 2.5e14, -1.25e8, 1.25e8, 0.2, 2.5e15, -99.0, 99.0, 5.0e-7, 0.0, 4.0e-6, 1.0e-9, 5.0e-8), nothing))
```
