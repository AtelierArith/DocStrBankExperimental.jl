```
GeoTable(domain; vtable, etable)
```

Create spatial geotable from a `domain`, a table `vtable` with geotable for the vertices, and a table `etable` with geotable for the elements.

## Examples

```julia
GeoTable(CartesianGrid(10,10),
  etable = (temperature=rand(100), pressure=rand(100))
)
```
