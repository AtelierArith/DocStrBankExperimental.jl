```
setfld!(D, kwargs...)
```

Sets fields of GMTdataset (or a vector of it), GMTgrid and GMTimage. Field names and field values are transmitted via `kwargs`

Example:     setfld!(D, geom=wkbPolygon)
