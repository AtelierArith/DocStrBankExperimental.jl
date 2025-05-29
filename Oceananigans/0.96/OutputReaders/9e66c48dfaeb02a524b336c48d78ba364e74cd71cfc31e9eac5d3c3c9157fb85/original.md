```
FieldDataset(filepath;
             architecture=CPU(), grid=nothing, backend=InMemory(), metadata_paths=["metadata"])
```

Returns a `Dict` containing a `FieldTimeSeries` for each field in the JLD2 file located at `filepath`. Note that model output **must** have been saved with halos.

# Keyword arguments

  * `backend`: Either `InMemory()` (default) or `OnDisk()`. The `InMemory` backend will

load the data fully in memory as a 4D multi-dimensional array while the `OnDisk()` backend will lazily load field time snapshots when the `FieldTimeSeries` is indexed linearly.

  * `metadata_paths`: A list of JLD2 paths to look for metadata. By default it looks in `file["metadata"]`.
  * `grid`: May be specified to override the grid used in the JLD2 file.
  * `reader_kw`: A named tuple or dictionary of keyword arguments to pass to the reader              (currently only JLD2) to be used when opening files.
