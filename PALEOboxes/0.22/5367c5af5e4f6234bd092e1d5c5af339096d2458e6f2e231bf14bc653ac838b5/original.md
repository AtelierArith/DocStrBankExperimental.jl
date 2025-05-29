```
copytofield!(
    values,
    FieldData::Type{<:AbstractData},
    data_dims::Tuple{Vararg{NamedDimension}},
    Space::Type{<:AbstractSpace},
    cellrange, 
    src, 
    soff
) -> num_copied::Int
```

Copy from `src` Array starting at index `soff` to Field.values `values` for spatial region defined by `cellrange`.

Number of values over whole Domain should equal degrees-of-freedom returned by [`dof_values`](@ref)

Required if this `FieldData` type needs to provide values for a numerical solver.
