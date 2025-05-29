```
SurfaceWaterRateTarget(q)
```

Well target of specified water rate with value `q` at surface conditions.

Often used for both [`InjectorControl`](@ref) [`ProducerControl`](@ref). If used for production it is important to also impose limits, as the well rate may become very high if there is little water present.
