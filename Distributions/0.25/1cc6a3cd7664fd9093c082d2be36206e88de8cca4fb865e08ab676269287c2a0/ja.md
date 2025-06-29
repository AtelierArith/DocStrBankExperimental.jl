```
pdf!(out, d::Distribution{ArrayLikeVariate{N}}, x) where {N}
```

分布 `d` の確率密度関数をコレクション `x` のすべての要素で評価し、結果を `out` に保存します。

この関数は、`out` のサイズが `d` と `x` と互換性があるかどうかをチェックし、`x` のすべての要素が分布 `d` と互換性があるかどうかを確認します。これらのチェックは `@inbounds` を使用することで無効にできます。

ここで、`x` は次のようにすることができます。

  * 次元 `> N` の配列で、`size(x)[1:N] == size(d)` であるか、または
  * 次元 `N` の配列の配列 `xi` で、`size(xi) == size(d)` であるか。

# 実装

`pdf!` の代わりに、`out` と `x` のサイズをチェックする必要がない `_pdf!(out, d, x)` を実装するべきです。しかし、`_pdf!(out, d, x)` のデフォルト定義は通常 `logpdf!` にフォールバックするため、`logpdf!` を実装するだけで十分です。

参照: [`logpdf!`](@ref).
