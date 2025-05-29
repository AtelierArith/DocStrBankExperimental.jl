```
Observable(t, name; keyargs...)
```

Create an observable of type `t`.

The following keywords are allowed:

  * `alloc`: preallocated size of time series container
  * `outfile`: default HDF5/JLD output file for io operations
  * `group`: target path within `outfile`
  * `inmemory`: wether to keep the time series in memory or on disk
  * `meantype`: type of the mean (should be compatible with measurement type `t`)

See also [`Observable`](@ref).
