```
segy_scan(dirs::Array{String,1}, filt::String, keys::Array{String,1}, blocksize::Int;
          chunksize::Int = CHUNKSIZE,
          pool::WorkerPool = WorkerPool(workers()),
          verbosity::Int = 1)
```

Scans all files whose name contains `filt` in each directory of `dirs` using `blocksize`.
