```
ft_printf(ftv_str::Union{String, Vector{String}}, [columns::AbstractVector{Int}]) -> Function
```

Apply the formats `ftv_str` (see the `Printf` standard library) to the elements in the columns `columns`.

If `ftv_str` is a `Vector`, `columns` must be also be a `Vector` with the same number of elements. If `ftv_str` is a `String`, and `columns` is not specified (or is empty), the format will be applied to the entire table.  Otherwise, if `ftv_str` is a `String` and `columns` is a `Vector`, the format will be applied only to the columns in `columns`.

!!! info
    This formatter will be applied only to the cells that are of type `Number`.

