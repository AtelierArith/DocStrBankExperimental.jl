```
segy_scan(dir::String, filt::String, keys::Array{String,1},
          chunksize::Int = CHUNKSIZE,
          pool::WorkerPool = WorkerPool(workers()),
          verbosity::Int = 1)
```

If no `blocksize` is specified, the scanner automatically detects source locations and returns blocks of continguous traces for each source location, but each block no larger then CHUNKSIZE. 
