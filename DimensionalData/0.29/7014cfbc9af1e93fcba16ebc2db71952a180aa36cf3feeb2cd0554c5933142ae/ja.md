```
refdims(x, [dims::Tuple]) => Tuple{Vararg{Dimension}}
refdims(x, dim) => Dimension
```

他の配列のスライスまたはビューである配列の参照次元。

`slicedims(a, dims)` は、現在の新しい次元と新しい参照次元を含むタプルを返します。Refdimsはフィールドに保存することも、主にプロットにコンテキストを提供するために破棄することもできます。refdimsを無視すると、単にいくつかのキャプションが空のままになります。

デフォルトは空の `Tuple` `()` を返すことです。
