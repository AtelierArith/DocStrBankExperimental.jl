```
timeseries_frommemory_flat(filename::AbstractString, group::AbstractString)
```

HDF5/JLDファイルのメモリダンプ（`inmemory==false`）から時系列をロードします。

時系列のチャンクをロードして連結します。出力は、最後の次元がモンテカルロ時間に対応する高次元配列になります。
