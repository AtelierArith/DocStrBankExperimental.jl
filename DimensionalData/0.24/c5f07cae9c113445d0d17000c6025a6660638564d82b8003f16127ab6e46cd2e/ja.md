```
dims(x, [dims::Tuple]) => Tuple{Vararg{Dimension}}
dims(x, dim) => Dimension
```

オブジェクトの軸または基になるデータの列に一致する順序で、`Dimension`のタプルを返します。

`dims`は`Dimension`、`Dimension`型、または`Dim{Symbol}`のための`Symbols`であることができます。

デフォルトは`nothing`を返します。
