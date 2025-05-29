```
SurfaceGasRateTarget(q)
```

Well target of specified gas rate with value `q` at surface conditions.

Often used for both [`InjectorControl`](@ref) [`ProducerControl`](@ref). Abbreviated as GRAT in some settings. If used for production it is important to also impose limits, as the well rate may become very high if there is little gas present.
