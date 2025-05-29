```
copyfieldto!(
    dest,
    doff, 
    values, 
    FieldData::Type{<:AbstractData}, 
    data_dims::Tuple{Vararg{NamedDimension}}, 
    Space::Type{<:AbstractSpace}, 
    cellrange
) -> num_copied::Int
```

Copy Field.values `values` from spatial region defined by `cellrange`, to `dest` Array starting at index `doff`.

Number of values over whole Domain should equal degrees-of-freedom returned by [`dof_values`](@ref)

Required if this `FieldData` type needs to provide values for a numerical solver.
