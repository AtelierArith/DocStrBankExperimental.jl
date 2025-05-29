```
as_array_axis(arg) -> rng::ArrayAxis
```

配列の次元または範囲 `arg` を標準的な配列軸、すなわち `AbstractUnitRange{eltype(Dims)}` のインスタンスに変換します。`arg` が整数の場合、`Base.OneTo{eltype(Dims)}(arg)` が返されます。[`eltype(RelaxedArrayShape)`](@ref RelaxedArrayShape) は、`as_array_axis` が適用可能な型の和です。

また、[`as_array_axes`](@ref)、[`as_array_dim`](@ref)、および `Dims` も参照してください。
