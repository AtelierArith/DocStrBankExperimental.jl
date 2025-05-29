```
zonalmean(A::ClimArray [, W])
```

`A`の緯度平均を返します。[`OrthogonalSpace`](@ref)および[`CoordinateSpace`](@ref)の両方で機能します。オプションで統計的重み`W`を提供できます。これらは`A`と同じ`size`であるか、または`A`と同じ緯度構造を持つ必要があります。
