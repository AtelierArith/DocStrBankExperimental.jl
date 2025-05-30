```
OrdinalRange{T, S} <: AbstractRange{T}
```

要素の型 `T` と型 `S` の間隔を持つ順序範囲のスーパタイプ。ステップは常に [`oneunit`](@ref) の正確な倍数である必要があり、`T` は `oneunit` より小さい値を持つことができない「離散」型である必要があります。例えば、`Integer` や `Date` 型は適格ですが、`Float64` 型は適格ではありません（この型は `oneunit(Float64)` より小さい値を表すことができるため）。[`UnitRange`](@ref)、[`StepRange`](@ref)、およびその他の型はこのサブタイプです。
