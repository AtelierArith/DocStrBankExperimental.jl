```
sample(d::TruncatedMVNormal, n::Integer, max_iter::Integer=10000)
```

分布 `d` から `n` サンプルをサンプリングします。

分布 `d` の次元 D に対して、D x n のサンプルの `Matrix` を返します。
