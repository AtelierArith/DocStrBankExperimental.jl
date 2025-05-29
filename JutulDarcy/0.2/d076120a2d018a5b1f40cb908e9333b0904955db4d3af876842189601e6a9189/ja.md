```
SurfaceWaterRateTarget(q)
```

指定された水率 `q` の井戸目標を表します。

通常、[`InjectorControl`](@ref) と [`ProducerControl`](@ref) の両方で使用されます。生産に使用する場合は、井戸の水率が水がほとんど存在しない場合に非常に高くなる可能性があるため、制限を課すことが重要です。
