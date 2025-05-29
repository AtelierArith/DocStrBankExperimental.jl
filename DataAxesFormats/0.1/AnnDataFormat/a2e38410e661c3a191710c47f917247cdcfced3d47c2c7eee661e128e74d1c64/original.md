```
anndata_as_daf(
    adata::Union{AnnData, AbstractString};
    [name::Maybe{AbstractString} = nothing,
    obs_is::Maybe{AbstractString} = nothing,
    var_is::Maybe{AbstractString} = nothing,
    X_is::Maybe{AbstractString} = nothing,
    unsupported_handler::AbnormalHandler = WarnHandler]
)::MemoryDaf
```

View `AnnData` as a `Daf` data set, specifically using a [`MemoryDaf`](@ref). This doesn't duplicate matrices or vectors, but acts as a view containing references to the same ones. Adding and/or deleting data in the view using the `Daf` API will not affect the original `adata`.

Any unsupported `AnnData` annotations will be handled using the `unsupported_handler`. By default, we'll warn about each and every such unsupported property.

If `adata` is a string, then it is the path of an `h5ad` file which is automatically loaded.

If not specified, the `name` will be the value of the "name" `uns` property, if it exists, otherwise, it will be "anndata".

If not specified, `obs_is` (the name of the "obs" axis) will be the value of the "obs_is" `uns` property, if it exists, otherwise, it will be "obs".

If not specified, `var_is` (the name of the "var" axis) will be the value of the "var_is" `uns` property, if it exists, otherwise, it will be "var".

If not specified, `X_is` (the name of the "X" matrix) will be the value of the "X_is" `uns` property, if it exists, otherwise, it will be "X".
