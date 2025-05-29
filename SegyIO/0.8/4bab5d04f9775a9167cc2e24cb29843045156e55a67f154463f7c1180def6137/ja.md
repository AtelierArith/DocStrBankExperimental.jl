```
segy_scan(dir::String, filt::String, keys::Array{String,1}, blocksize::Int; 
          chunksize::Int = CHUNKSIZE,
          pool::WorkerPool = WorkerPool(workers()),
          verbosity::Int = 1)

returns: SeisCon
```

`dir`内の`filt`に一致するファイルのヘッダーフィールド`keys`を、`blocksize`個の連続したトレースを含むブロックでスキャンします。ファイルのスキャンは`pool`内のワーカーに分散され、デフォルトのプールはすべてのワーカーです。

`chunksize`は、一度にメモリに読み込まれるデータのMB数を決定します。

`CHUNKSIZE`のデフォルトは2048MBです。

`verbosity`を0に設定すると、現在スキャン中のファイルに関する更新が無効になります。
