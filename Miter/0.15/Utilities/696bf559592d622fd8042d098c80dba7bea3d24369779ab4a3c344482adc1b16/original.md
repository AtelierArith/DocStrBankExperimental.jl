```julia
balanced_matrix(
    vector_or_itr;
    width_bias,
    row_major,
    width,
    height
)

```

Arrange elements of a vector (or iterable) in a `(height, width)` matrix, such that `width / height ≈ width_bias`. Extra elements are filled with `nothing`.

When `row_major = true` (default), elements are arranged row-major.

The purpose of this function is to make balanced displays, eg in [`Tableau`](@ref).

`width` and `height` can also be specified explicitly, in which case `width_bias` is not used.
