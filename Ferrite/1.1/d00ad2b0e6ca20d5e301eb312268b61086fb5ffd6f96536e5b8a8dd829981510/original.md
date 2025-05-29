```
add!(dh::DofHandler, name::Symbol, ip::Interpolation)
```

Add a field called `name` approximated by `ip` to the DofHandler `dh`.

The field is added to all cells of the underlying grid, use [`SubDofHandler`](@ref)s if the grid contains multiple cell types, or to add the field to subset of all the cells.
