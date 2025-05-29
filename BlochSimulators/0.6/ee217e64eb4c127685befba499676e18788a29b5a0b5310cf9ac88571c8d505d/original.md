```
EPGSimulator{T,Ns} <: BlochSimulator{T}
```

Abstract type of which all sequence simulators that are based on the EPG model will be a subtype. The parameter `T` should be a number type (e.g. `Float64`, `Float32`) and the tissueparameters that are used as input to the simulator should have the same number type. The parameter `Ns` corresponds to the maximum order of configuration states that are tracked in the simulations.
