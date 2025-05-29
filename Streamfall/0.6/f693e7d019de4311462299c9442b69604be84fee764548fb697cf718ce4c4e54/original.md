```
align_time_frame(timeseries::T...)
```

Subset an arbitrary number of DataFrames to their shared period of time.

Returns subsetted copy of data in same order as input.

# Example

```julia-repl
julia> climate, streamflow = align_time_frame(climate, streamflow)
```
