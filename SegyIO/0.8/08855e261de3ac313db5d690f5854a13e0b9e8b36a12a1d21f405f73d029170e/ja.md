```
segy_scan(dirs::Array{String,1}, filt::String, keys::Array{String,1},
          chunksize::Int = CHUNKSIZE,
          pool::WorkerPool = WorkerPool(workers()),
          verbosity::Int = 1)
```

`dirs`の各ディレクトリ内で`filt`を含む名前のすべてのファイルをスキャンします。
