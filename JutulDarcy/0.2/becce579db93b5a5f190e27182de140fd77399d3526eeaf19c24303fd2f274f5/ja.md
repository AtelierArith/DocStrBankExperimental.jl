```
SurfaceGasRateTarget(q)
```

指定されたガス流量 `q` の井戸目標を表します。

通常、[`InjectorControl`](@ref) と [`ProducerControl`](@ref) の両方で使用されます。一部の設定では GRAT と略されます。生産に使用する場合は、ガスがほとんど存在しないと井戸の流量が非常に高くなる可能性があるため、制限を課すことが重要です。
