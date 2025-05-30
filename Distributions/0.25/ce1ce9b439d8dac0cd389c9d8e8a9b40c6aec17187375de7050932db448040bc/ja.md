```
loglikelihood(d::Distribution{ArrayLikeVariate{N}}, x) where {N}
```

分布 `d` の対数尤度は、`x` に含まれるすべての変量に関して計算されます。

ここで、`x` は `rand(d, dims...)` および `rand!(d, x)` の任意の出力である可能性があります。例えば、`x` は次のようになります。

  * `size(x) == size(d)` の次元 `N` の配列、
  * `size(x)[1:N] == size(d)` の次元 `N + 1` の配列、または
  * `size(xi) == size(d)` の次元 `N` の配列の配列 `xi`。
