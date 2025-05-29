```
Field{FieldData <: AbstractData, Space <: AbstractSpace, V, N, Mesh <: AbstractMeshOrNothing}
Field(FieldData, data_dims::NTuple{N, NamedDimensions}, data_type, Space, mesh::AbstractMeshOrNothing; allocatenans)
Field(existing_values, FieldData, data_dims::NTuple{N, NamedDimension}, data_type::Union{DataType, Missing}, Space, mesh::AbstractMeshOrNothing)
```

A Field of `values::V` of type `FieldData <: AbstractData` defined on function space `Space` over grid of type `Mesh` and (optionally) with `N` `data_dims::NTuple{N, NamedDimensions}`.

`values::V` is usually Array or similar of elements with Type `data_type` and dimensions defined by `Space`, `Mesh` and `data_dims`, and is either created by [`allocate_values`](@ref) or supplied by `existing_values`.
