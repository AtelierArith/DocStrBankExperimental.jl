```
Cell(cs::CoordinateSystem{S}) = Cell{S}(cs)
Cell(cs::CoordinateSystem, unit::CoordinateUnits) = Cell{typeof(1.0unit)}(cs)
Cell{S}(cs::CoordinateSystem) where {S}
```

Construct a `Cell` from a `CoordinateSystem` by rendering its contents, reproducing the reference hierarchy.
