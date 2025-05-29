```
check_values(
    existing_values, 
    FieldData::Type{<:AbstractData},
    data_dims::Tuple{Vararg{NamedDimension}}, 
    data_type, 
    Space::Type{<:AbstractSpace}, 
    spatial_size::Tuple{Integer, Vararg{Integer}}
)
```

Check `existing_values` is of suitable type, size etc for use as `Field.values`, throw exception if not.
