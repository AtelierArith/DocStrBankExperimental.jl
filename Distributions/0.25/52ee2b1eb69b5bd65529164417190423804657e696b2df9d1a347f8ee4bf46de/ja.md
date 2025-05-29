```
cov(d::MatrixDistribution, flattened = Val(false))
```

4次元配列を計算します。その要素 `(i, j, k, l)` は `cov(X[i,j], X[k, l])` です。
