```
allocate_values(
    FieldData::Type{<:AbstractData}, data_dims::Tuple{Vararg{NamedDimension}}, data_type, Space::Type{<:AbstractSpace}, spatial_size::Tuple;
    allocatenans::Bool,
) -> values::V
```

`Field.values::V`（例えば、`data_type`の要素の配列）を、`spatial_size`と`data_dims`で定義された次元を持つ`FieldData`のために割り当てます。
