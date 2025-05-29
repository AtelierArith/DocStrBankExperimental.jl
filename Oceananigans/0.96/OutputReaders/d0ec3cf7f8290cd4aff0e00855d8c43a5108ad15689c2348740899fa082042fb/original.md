```
FieldTimeSeries(path, name;
                backend = InMemory(),
                architecture = nothing,
                grid = nothing,
                location = nothing,
                boundary_conditions = UnspecifiedBoundaryConditions(),
                time_indexing = Linear(),
                iterations = nothing,
                times = nothing,
                reader_kw = Dict{Symbol, Any}())
```

Return a `FieldTimeSeries` containing a time-series of the field `name` load from JLD2 output located at `path`.

# Keyword arguments

  * `backend`: `InMemory()` to load data into a 4D array, `OnDisk()` to lazily load data from disk            when indexing into `FieldTimeSeries`.
  * `grid`: A grid to associate with the data, in the case that the native grid was not serialized         properly.
  * `iterations`: Iterations to load. Defaults to all iterations found in the file.
  * `times`: Save times to load, as determined through an approximate floating point          comparison to recorded save times. Defaults to times associated with `iterations`.          Takes precedence over `iterations` if `times` is specified.
  * `reader_kw`: A named tuple or dictionary of keyword arguments to pass to the reader              (currently only JLD2) to be used when opening files.
