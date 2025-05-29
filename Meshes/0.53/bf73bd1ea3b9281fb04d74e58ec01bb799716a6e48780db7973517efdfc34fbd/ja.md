```
MetricBall(radii, rotation=I)
MetricBall(radius, metric=Euclidean())
```

メトリックボールは、`metric` と `radii` のセットを用いて表現できる近傍です。主な例としては、ユークリッドボールとマハラノビス（楕円体）ボールがあります。

複数の `radii` が提供される場合、それらは [Rotations.jl](https://github.com/JuliaGeometry/Rotations.jl) パッケージからの `rotation` 指定によって回転させることができます。あるいは、単一の `radius` とともに [Distances.jl](https://github.com/JuliaStats/Distances.jl) パッケージからの `metric` を指定することもできます。

## 例

半径 `1.0` の N 次元ユークリッドボール：

```julia
julia> MetricBall(1.0)
```

軸に整列した半径 `(3.0, 2.0, 1.0)` の 3D 楕円体：

```julia
julia> MetricBall((3.0, 2.0, 1.0))
```
