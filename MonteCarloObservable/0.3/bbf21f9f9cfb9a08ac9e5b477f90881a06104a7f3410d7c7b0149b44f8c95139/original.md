```
timeseries_frommemory_flat(filename::AbstractString, group::AbstractString)
```

Load time series from memory dump (`inmemory==false`) in HDF5/JLD file.

Will load and concatenate time series chunks. Output will be higher-dimensional array whose last dimension corresponds to Monte Carlo time.
