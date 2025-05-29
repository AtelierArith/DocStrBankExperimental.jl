```
DimIndices <: AbstractArray

DimIndices(x)
DimIndices(dims::Tuple)
DimIndices(dims::Dimension)
```

`CartesianIndices`のようですが、`Dimension`用です。`dims`の軸インデックスのすべての組み合わせに対して、`Dimension(i)`の`Tuple`の`Array`として動作します。

これは、配列の任意の次元を表示/インデックスするために使用でき、特に`otherdims`と組み合わせると、未知の次元のインデックスを反復処理するのに便利です。
