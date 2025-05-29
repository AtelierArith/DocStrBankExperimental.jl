```
label(x) => String
label(x, dims::Tuple) => NTuple{N,String}
label(x, dim) => String
label(xs::Tuple) => NTuple{N,String}
```

データまたは次元のプロットラベルを取得します。これには、名前と単位が存在する場合はそれらが含まれ、プロットに表示されるべきその他の情報も含まれます。

第二引数 `dims` は、`Dimension`、`Dimension` 型、または `Dim{Symbol}` のための `Symbols` である可能性があります。
