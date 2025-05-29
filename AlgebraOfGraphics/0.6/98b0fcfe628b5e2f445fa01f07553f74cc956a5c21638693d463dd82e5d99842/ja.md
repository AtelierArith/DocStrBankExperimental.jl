```
draw(p::PaginatedLayers, i::Int; kws...)
```

`PaginatedLayers` `p`のi番目の要素を描画し、`FigureGrid`を返します。キーワード`kws`は、基盤となる`draw`呼び出しに渡されます。

要素の数は`length(p)`を使用して取得できます。
