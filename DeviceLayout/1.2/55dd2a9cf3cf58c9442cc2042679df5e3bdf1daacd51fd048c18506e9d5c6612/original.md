```
elements(s::GeometryStructure)
```

Return a vector of `GeometryEntity` in the structure.

For a `Cell`, these are `Polygon`s. For a `CoordinateSystem`, these can be any `GeometryEntity`.
