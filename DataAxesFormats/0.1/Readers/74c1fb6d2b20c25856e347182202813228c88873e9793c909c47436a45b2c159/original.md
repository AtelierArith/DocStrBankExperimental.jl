```
axis_vector(
    daf::DafReader,
    axis::AbstractString;
    [default::Union{Nothing, UndefInitializer} = undef]
)::Maybe{AbstractVector{<:AbstractString}}
```

The array of unique names of the entries of some `axis` of `daf`. This is similar to doing [`get_vector`](@ref) for the special `name` property, except that it returns a simple vector (array) of strings instead of a `NamedVector`.

If `default` is `undef` (the default), this verifies the `axis` exists in `daf`. Otherwise, the `default` is `nothing`, which is returned if the `axis` does not exist.
