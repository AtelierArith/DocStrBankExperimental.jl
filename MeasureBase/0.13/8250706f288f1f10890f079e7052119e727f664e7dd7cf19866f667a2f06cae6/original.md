```
logdensityof(m::AbstractMeasure, x)
```

Compute the log-density of the measure `m` at `x`. Density is always relative, but `DensityInterface.jl` does not account for this. For compatibility with this, `logdensityof` for a measure is always implicitly relative to [`rootmeasure(x)`](@ref rootmeasure). 

`logdensityof` works by first computing `insupport(m, x)`. If this is true, then `unsafe_logdensityof` is called. If `insupport(m, x)` is known to be `true`, it can be a little faster to directly call `unsafe_logdensityof(m, x)`. 

To compute log-density relative to `basemeasure(m)` or *define* a log-density (relative to `basemeasure(m)` or another measure given explicitly), see `logdensity_def`. 

To compute a log-density relative to a specific base-measure, see `logdensity_rel`. 
