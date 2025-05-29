```
Snapshots(path::String)
```

A lazy iterator to access snapshots in the InPartS data file at `path`.

Indexing syntax `Snapshots(path)[i]` will open the file and attempt to load the `i`th snapshot using [`readsim`](@ref). Indexing with a unit range `Snapshots(path)[i:j]` will return a `Snapshots` struct with modified `firstindex` and `lastindex`. Note that bounds checking may not be performed here, as the file isn't opened and therefore the last snapshot index cannot be determined if it isn't already known from a previous file access. Therefore, the resulting `Snapshots` may be invalid.

Iteration is also supported, but keep in mind that the data file will be opened and closed in every single iteration.

Requires your data file to use zero indexed sequentially numbered snapshots (as is the case if you used a [`SaveCallback`](@ref)).
