```
FieldTimeSeries{LX, LY, LZ}(grid::AbstractGrid [, times=()]; kwargs...)
```

Construct a `FieldTimeSeries` on `grid` and at `times`.

# Keyword arguments

  * `indices`: spatial indices
  * `backend`: backend, `InMemory(indices=Colon())` or `OnDisk()`
  * `path`: path to data for `backend = OnDisk()`
  * `name`: name of field for `backend = OnDisk()`
