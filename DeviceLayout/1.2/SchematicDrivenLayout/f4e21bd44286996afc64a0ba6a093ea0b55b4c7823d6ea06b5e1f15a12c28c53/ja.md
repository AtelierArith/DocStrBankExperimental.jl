```
Cell{S,T}(cs::CoordinateSystem, target::LayoutTarget; kwargs...) where {S,T}
Cell{S}(cs::CoordinateSystem, target::LayoutTarget; kwargs...) where {S}
Cell(cs::CoordinateSystem, unit::CoordinateUnits, target::LayoutTarget; kwargs...)
```

新しいセルを作成し、`target`に従って`cs`をレンダリングします。

詳細については[`LayoutTarget`](@ref)のドキュメントを参照してください。
