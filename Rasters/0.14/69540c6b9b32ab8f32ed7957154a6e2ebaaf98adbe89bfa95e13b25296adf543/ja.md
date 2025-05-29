```
disaggregate!(dst::AbstractRaster, src::AbstractRaster, scale)
```

配列 `src` をスケールによって配列 `dst` に分解します。

  * `scale`: 集約因子で、`Int`、各次元の `Int` の `Tuple`、または全次元を意味する `:` コロンで指定できます。また、通常 `getindex` で使用できる任意の `Dimension`、`Selector`、または `Int` の組み合わせを使用できます。キーが次元名の `Pair` または `NamedTuple` の `Tuple` も機能します。`Selector` を使用すると、インデックスの開始からの距離によってスケールが決まります。セレクタは最初のオフセットを見つけ、残りの部分に対して同じ集約サイズを繰り返します。
