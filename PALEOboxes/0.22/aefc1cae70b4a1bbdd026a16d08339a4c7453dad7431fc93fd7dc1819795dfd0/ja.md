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

`existing_values`が`Field.values`として使用するのに適した型、サイズなどであることを確認し、そうでない場合は例外をスローします。
