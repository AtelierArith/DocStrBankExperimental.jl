```
metadata(x) => (オブジェクトメタデータ)
metadata(x, dims::Tuple)  => Tuple (次元メタデータ)
metadata(xs::Tuple) => Tuple
```

オブジェクトまたは指定された次元のメタデータを返します。

第二引数 `dims` は `Dimension`、`Dimension` タイプ、または `Dim{Symbol}` のための `Symbols` であることができます。
