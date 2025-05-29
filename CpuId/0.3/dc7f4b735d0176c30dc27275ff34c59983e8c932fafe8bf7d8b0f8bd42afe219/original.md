```
cpufeature( feature::Symbol ) ::Bool
cpufeature( feature::CpuFeature ) ::Bool
```

Query the CPU whether it supports the given feature.  For fast checking provide directly the `CpuFeature` defined as a global const in `CpuId`. Explicitly typed `CpuFeature`s got by the same name as the corresponding symbols.  Valid symbols are available from `keys(CpuId.CpuFeatureDescription)`.
