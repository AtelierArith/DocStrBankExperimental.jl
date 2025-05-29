```
spdiff(dims::Dims; order=1, kwargs...)
```

`length(dims)` のスパース有限差分行列の `Vector` を返します。各次元に対して、順序は `order` です。

通常、出力されたベクトルを `vcat` して、多次元配列の `vec` に適したスパース有限差分行列を作成します。

`kwargs` は `spdiff1`（`order = 1` の場合）または `spdiff2`（`order = 2` の場合）に渡されます。これらの関数は各次元ごとに一度呼び出されます。オプションは `ending` と `T` です。

例:

  * `spdiff((4,5,6))[1] == kron(I(6*5), spdiff1(4))`
  * `spdiff((4,5,6); order=1)[2] == kron(I(6), spdiff1(5), I(4))`
  * `spdiff((4,5,6); order=2)[3] == kron(spdiff2(6), I(4*5))`
