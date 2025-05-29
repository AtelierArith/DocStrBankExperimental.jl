```
segy_scan(dir::String, filt::String, keys::Array{String,1},
          chunksize::Int = CHUNKSIZE,
          pool::WorkerPool = WorkerPool(workers()),
          verbosity::Int = 1)
```

`blocksize`が指定されていない場合、スキャナーは自動的にソースの位置を検出し、各ソースの位置に対して連続したトレースのブロックを返しますが、各ブロックはCHUNKSIZEを超えることはありません。
