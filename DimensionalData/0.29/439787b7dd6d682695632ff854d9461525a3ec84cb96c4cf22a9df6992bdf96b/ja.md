```
name(x) => Symbol
name(xs:Tuple) => NTuple{N,Symbol}
name(x, dims::Tuple) => NTuple{N,Symbol}
name(x, dim) => Symbol
```

配列または次元、またはどちらかのタプルの名前をシンボルとして取得します。

第二引数 `dims` は `Dimension`、`Dimension` 型、または `Dim{Symbol}` のための `Symbols` である可能性があります。
