```
as_array_dim(arg) -> dim::eltype(Dims)
```

は、配列の次元または範囲 `arg` を標準的な配列次元、すなわち `eltype(Dims)` に変換します。`arg` が単位ステップ範囲である場合、その長さが返されます。 [`eltype(RelaxedArrayShape)`](@ref RelaxedArrayShape) は、`as_array_dim` が適用可能な型の和です。

また、[`as_array_size`](@ref)、[`as_array_axis`](@ref)、および `Dims` も参照してください。
