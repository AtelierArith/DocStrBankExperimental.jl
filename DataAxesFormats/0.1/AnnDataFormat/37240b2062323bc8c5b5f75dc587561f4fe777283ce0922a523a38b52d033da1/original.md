```
daf_as_anndata(
    daf::DafReader;
    [obs_is::Maybe{AbstractString} = nothing,
    var_is::Maybe{AbstractString} = nothing,
    X_is::Maybe{AbstractString} = nothing,
    h5ad::Maybe{AbstractString} = nothing]
)::AnnData
```

View the `daf` data set as `AnnData`. This doesn't duplicate matrices or vectors, but acts as a view containing references to the same ones. Adding and/or deleting data in the view using the `AnnData` API will not affect the original `daf` data set.

If specified, the result is also written to an `h5ad` file.

If not specified, `obs_is` (the name of the "obs" axis) will be the value of the "obs_is" scalar property, if it exists, otherwise, it will be "obs".

If not specified, `var_is` (the name of the "var" axis) will be the value of the "var_is" scalar property, if it exists, otherwise, it will be "var".

If not specified, `X_is` (the name of the "X" matrix) will be the value of the "X_is" scalar property, if it exists, otherwise, it will be "X".

Each of the final `obs_is`, `var_is`, `X_is` values is stored as unstructured annotations, unless the default value ("obs", "var", "X") is used.

All scalar properties, vector properties of the chosen "obs" and "var" axes, and matrix properties of these axes, are stored in the returned new `AnnData` object.
