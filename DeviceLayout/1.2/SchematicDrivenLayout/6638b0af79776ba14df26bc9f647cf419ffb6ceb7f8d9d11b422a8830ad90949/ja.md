```
render!(cs::AbstractCoordinateSystem, cs2::GeometryStructure, target::LayoutTarget; kwargs...)
```

`cs2`を`cs`にレンダリングし、メタデータをレイヤーにマッピングし、`target`によってレンダリングオプションを指定します。

詳細については[`LayoutTarget`](@ref)のドキュメントを参照してください。
