```
extract_sources(::SourceFinder, data, [error]; sorted=true)
```

Uses `method` to find and extract point-like sources.

Returns a `TypedTables.Table` with positions and information related to the `method`. For instance, using `PeakMesh` returns a table a column for the peak values.

`data` is assumed to be background-subtracted. If `error` is provided it will be propagated into the detection algorithm. If `sorted` is `true` the sources will be sorted by their amplitude.

# See Also

  * [Source Detection Algorithms](@ref)
