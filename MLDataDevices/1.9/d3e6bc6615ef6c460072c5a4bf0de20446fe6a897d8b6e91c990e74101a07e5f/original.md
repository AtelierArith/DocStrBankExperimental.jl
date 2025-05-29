```
default_device_rng(::AbstractDevice)
```

Returns the default RNG for the device. This can be used to directly generate parameters and states on the device using [WeightInitializers.jl](https://github.com/LuxDL/WeightInitializers.jl).
