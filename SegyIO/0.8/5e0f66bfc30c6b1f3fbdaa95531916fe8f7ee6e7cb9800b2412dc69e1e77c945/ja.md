```
segy_scan(dirs::Array{String,1}, filt::String, keys::Array{String,1}, blocksize::Int;
          chunksize::Int = CHUNKSIZE,
          pool::WorkerPool = WorkerPool(workers()),
          verbosity::Int = 1)
```

`dirs`の各ディレクトリ内で名前に`filt`を含むすべてのファイルを`blocksize`を使用してスキャンします。
