```
get_spatial_index(pos, property::AbstractArray, model::ABM)
```

連続エージェントの位置を、[`ContinuousSpace`](@ref) 上の空間フィールドの離散化を表す `property` の適切な `index` に変換します。

`property` の次元と連続空間は一致する必要はありません。`property` が空間よりも次元が低い場合（例：3D空間における表面特性を表す場合）、`pos` の前の次元がインデックスに使用されます。
