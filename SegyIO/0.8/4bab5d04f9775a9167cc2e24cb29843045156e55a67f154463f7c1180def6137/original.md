```
segy_scan(dir::String, filt::String, keys::Array{String,1}, blocksize::Int; 
          chunksize::Int = CHUNKSIZE,
          pool::WorkerPool = WorkerPool(workers()),
          verbosity::Int = 1)

returns: SeisCon
```

Scan header fields `keys` of files in `dir` matching the filter `filt` in blocks containing `blocksize` continguous traces. The scanning of files is distributed to workers in `pool`, the default pool is all workers.

`chunksize` determines how many MB of data will be loaded into memory at a time.

`CHUNKSIZE` defaults to 2048MB.

`verbosity` set to 0 silences updates on the current file being scanned.
