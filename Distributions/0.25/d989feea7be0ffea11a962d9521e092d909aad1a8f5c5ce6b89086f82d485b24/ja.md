```
logpdf(d::Distribution{ArrayLikeVariate{N}}, x) where {N}
```

分布 `d` の確率密度関数の対数をコレクション `x` のすべての要素で評価します。

この関数は、`x` のすべての要素が分布 `d` と互換性のあるサイズであるかをチェックします。このチェックは `@inbounds` を使用することで無効にできます。

ここで、`x` は次のいずれかです。

  * `size(x)[1:N] == size(d)` を満たす次元 `> N` の配列、または
  * `size(xi) == size(d)` を満たす次元 `N` の配列の配列 `xi`。
