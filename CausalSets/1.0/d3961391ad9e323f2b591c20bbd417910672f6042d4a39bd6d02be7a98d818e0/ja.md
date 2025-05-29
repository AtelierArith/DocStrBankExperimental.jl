```
BoxBoundary{N}(edges::Tuple{Coordinate{N}, Coordinate{N}}) <: AbstractBoundary{N}
```

`edges`によって区切られた長方形のボックスで指定された領域。これは平坦な多様体に対してのみ意味を持つため、現在は[`MinkowskiManifold`](@ref)および[`TorusManifold`](@ref)に対して実装されています。

この境界が[`MinkowskiManifold`](@ref)で使用される場合、下限`edges[1][i]`はすべての軸`1 ≤ i ≤ N`に対して`edges[2][i]`よりも小さくする必要があります。[`TorusManifold`](@ref)の場合、下限は上限よりも高くなることができます。この場合、境界はトーラスを回り込みます。
