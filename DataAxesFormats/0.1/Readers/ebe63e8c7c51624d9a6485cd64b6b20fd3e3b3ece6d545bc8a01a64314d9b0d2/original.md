```
get_vector(
    daf::DafReader,
    axis::AbstractString,
    name::AbstractString;
    [default::Union{StorageScalar, StorageVector, Nothing, UndefInitializer} = undef]
)::Maybe{NamedVector}
```

Get the vector property with some `name` for some `axis` in `daf`. The names of the result are the names of the vector entries (same as returned by [`axis_vector`](@ref)). The special property `name` returns an array whose values are also the (read-only) names of the entries of the axis.

This first verifies the `axis` exists in `daf`. If `default` is `undef` (the default), this first verifies the `name` vector exists in `daf`. Otherwise, if `default` is `nothing`, it will be returned. If it is a [`StorageVector`](@ref), it has to be of the same size as the `axis`, and is returned. If it is a [`StorageScalar`](@ref). Otherwise, a new `Vector` is created of the correct size containing the `default`, and is returned.
