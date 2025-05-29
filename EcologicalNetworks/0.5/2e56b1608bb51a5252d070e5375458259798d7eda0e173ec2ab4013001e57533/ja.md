```
svd_truncated(N::BinaryNetwork, rnk::Integer=3)
```

バイナリネットワーク `N` の隣接行列 `A` が次元 `n × m` の場合、`svd_truncated(A)` は、次元がそれぞれ `n × rank` と `rank × m` の二つの行列 `Left` と `Right` を返します。これは、ネットワーク `N` の RDPG 空間における種の表現に対応しています。

特異値分解は `LinearAlgebra` の `svd` を使用して計算され、次のようになります。

`A = U * Diagonal(S) * V = U * Diagonal(√S) * Diagonal(√S) * V`.

切り捨ては、`U * Diagonal(√S)` の最初の `rank` 列と、`Diagonal(√S) * V` の最初の `rank` 行を保持します。

私たちは、`A ≃ Left * Right` であることがわかります（この近似は特定の意味で最適です）。

#### 参考文献

Dalla Riva, G.V. and Stouffer, D.B., 2016. Exploring the evolutionary signature of food webs' backbones using functional traits. Oikos, 125(4), pp.446-456. https://doi.org/10.1111/oik.02305 ```
