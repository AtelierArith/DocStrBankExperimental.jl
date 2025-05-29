```
Field{FieldData <: AbstractData, Space <: AbstractSpace, V, N, Mesh <: AbstractMeshOrNothing}
Field(FieldData, data_dims::NTuple{N, NamedDimensions}, data_type, Space, mesh::AbstractMeshOrNothing; allocatenans)
Field(existing_values, FieldData, data_dims::NTuple{N, NamedDimension}, data_type::Union{DataType, Missing}, Space, mesh::AbstractMeshOrNothing)
```

関数空間 `Space` 上のグリッドタイプ `Mesh` に定義された `FieldData <: AbstractData` 型の `values::V` のフィールドであり、（オプションで）`N` `data_dims::NTuple{N, NamedDimensions}` を持ちます。

`values::V` は通常、`Space`、`Mesh`、および `data_dims` によって定義された次元を持つ `data_type` 型の要素の配列またはそれに類似したものであり、[`allocate_values`](@ref) によって作成されるか、`existing_values` によって提供されます。
