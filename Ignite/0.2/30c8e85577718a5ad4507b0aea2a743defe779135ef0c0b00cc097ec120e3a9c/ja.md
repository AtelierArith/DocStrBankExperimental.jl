```julia
abstract type AbstractFiringEvent <: Ignite.AbstractEvent
```

イベントハンドラを [`fire_event!`](@ref) を介してトリガーできるすべてのイベントの抽象スーパタイプです。
