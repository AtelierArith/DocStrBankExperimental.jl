```
timeseries_frommemory(filename::AbstractString, group::AbstractString)
```

HDF5/JLDファイルのメモリダンプ（`inmemory==false`）から時系列をロードします。

時系列チャンクをロードして連結します。出力は測定値のベクトルになります。
