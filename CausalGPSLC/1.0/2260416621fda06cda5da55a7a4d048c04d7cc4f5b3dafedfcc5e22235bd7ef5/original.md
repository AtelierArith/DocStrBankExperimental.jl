```
GPSLCObject
```

This is the struct in CausalGPSLC.jl that contains the data, hyperparamters, prior parameters, and posterior samples. It provides the primary interfaces to abstract the internals of CausalGPSLC away from the higher-order functions like [`sampleITE`](@ref), [`sampleSATE`](@ref), and [`predictCounterfactualEffects`](@ref).

Returned by [`gpslc`](@ref)
