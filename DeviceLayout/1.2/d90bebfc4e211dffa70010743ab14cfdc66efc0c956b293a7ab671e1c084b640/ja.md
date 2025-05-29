```
Cell(cs::CoordinateSystem{S}) = Cell{S}(cs)
Cell(cs::CoordinateSystem, unit::CoordinateUnits) = Cell{typeof(1.0unit)}(cs)
Cell{S}(cs::CoordinateSystem) where {S}
```

`CoordinateSystem`から`Cell`を構築するには、その内容をレンダリングし、参照階層を再現します。
