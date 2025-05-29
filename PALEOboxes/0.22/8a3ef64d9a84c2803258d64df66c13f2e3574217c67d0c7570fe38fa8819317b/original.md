```
allocate_values(
    FieldData::Type{<:AbstractData}, data_dims::Tuple{Vararg{NamedDimension}}, data_type, Space::Type{<:AbstractSpace}, spatial_size::Tuple;
    allocatenans::Bool,
) -> values::V
```

allocate `Field.values::V` (eg an Array of elements with Type `data_type`) for `FieldData` with dimensions defined by `spatial_size` and `data_dims`
