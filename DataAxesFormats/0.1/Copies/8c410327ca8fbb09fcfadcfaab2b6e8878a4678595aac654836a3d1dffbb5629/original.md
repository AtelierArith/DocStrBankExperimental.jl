```
copy_all!(;
    destination::DafWriter,
    source::DafReader
    [empty::Maybe{EmptyData} = nothing,
    dtypes::Maybe{DataTypes} = nothing,
    overwrite::Bool = false,
    relayout::Bool = true]
)::Nothing
```

Copy all the content of a `source` [`DafReader`](@ref) into a `destination` [`DafWriter`](@ref). If `overwrite`, this will overwrite existing data in the target. If `relayout`, matrices will be stored in the target both layouts, regardless of how they were stored in the source.

This will create target axes that exist in only in the source, but will **not** overwrite existing target axes, regardless of the value of `overwrite`. An axis that exists in the target must be identical to, or be a subset of, the same axis in the source.

If the source has axes which are a subset of the same axes in the target, then you must specify a dictionary of values for the `empty` entries that will be created in the target when copying any vector and/or matrix properties. This is specified using a `(axis, property) => value` entry for specifying an `empty` value for a vector property and a `(rows_axis, columns_axis, property) => entry` for specifying an `empty` value for a matrix property. The order of the axes for matrix properties doesn't matter (the same `empty` value is automatically used for both axes orders).

If `dtype` is specified, the copied data of the matching property is converted to the specified data type.

If a [`TensorKey`](@ref) is specified, this will create an matrix full of the `empty` value for any entries of the main axis which exist in the destination but do not exist in the source.
