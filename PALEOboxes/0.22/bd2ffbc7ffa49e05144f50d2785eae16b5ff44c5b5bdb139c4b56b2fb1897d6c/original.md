```
add_field_vec!(
    dest, 
    FieldData::Type{<:AbstractData}, 
    data_dims::Tuple{Vararg{NamedDimension}}, 
    Space::Type{<:AbstractSpace}, 
    a, 
    cellrange,
    src, 
    soff
) -> num_added::Int
```

Implement `dest += a*src` where `dest` is a Field.values, `src` is an Array, `a` is a number, over region defined by `cellrange`, starting at index `soff` in `src`.

Returns number of elements of `src` used.

See  [`copytofield!`](@ref), [`copyfieldto!`](@ref) for the relationship between Array `src` and Field values `dest`.
