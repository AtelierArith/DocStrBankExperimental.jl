```
get_matrix(
    daf::DafReader,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString;
    [default::Union{StorageReal, StorageMatrix, Nothing, UndefInitializer} = undef,
    relayout::Bool = true]
)::Maybe{NamedMatrix}
```

Get the column-major matrix property with some `name` for some `rows_axis` and `columns_axis` in `daf`. The names of the result axes are the names of the relevant axes entries (same as returned by [`axis_vector`](@ref)).

If `relayout` (the default), then if the matrix is only stored in the other memory layout (that is, with flipped axes), then automatically call [`relayout!`](@ref) to compute the result. If `daf` isa [`DafWriter`](@ref), then store the result for future use; otherwise, just cache it as [`MemoryData`](@ref CacheGroup). This may lock up very large amounts of memory; you can call [`empty_cache!`](@ref) to release it.

This first verifies the `rows_axis` and `columns_axis` exist in `daf`. If `default` is `undef` (the default), this first verifies the `name` matrix exists in `daf`. Otherwise, if `default` is `nothing`, it is returned. If `default` is a `StorageMatrix`, it has to be of the same size as the `rows_axis` and `columns_axis`, and is returned. Otherwise, a new `Matrix` is created of the correct size containing the `default`, and is returned.
