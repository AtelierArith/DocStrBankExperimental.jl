```
laplacian_matrix(g, dir::Symbol=:out, T::DataType=Int)
```

グラフ `g` のスパース [ラプラシアン行列](https://en.wikipedia.org/wiki/Laplacian_matrix) を返します。インデックスは `[u, v]` の頂点によって指定されます。`dir` は `:in, :out` または `:all` でなければなりません。
