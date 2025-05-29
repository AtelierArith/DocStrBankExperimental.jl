```
AbstractNeighborhood
```

与えられた点の近傍を決定するためのメソッドのスーパークラス。

具体的なサブタイプ：

  * `FixedMassNeighborhood(K::Int)` : 点の近傍は、その点の `K` 最近傍から構成されます。
  * `FixedSizeNeighborhood(ε::Real)` : 点の近傍は、その点からの距離が < `ε` のすべての近傍から構成されます。

詳細については [`neighborhood`](@ref) を参照してください。
