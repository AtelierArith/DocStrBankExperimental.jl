```
write_to_file(
    model::Model,
    filename::String;
    format::MOI.FileFormats.FileFormat = MOI.FileFormats.FORMAT_AUTOMATIC,
    kwargs...,
)
```

Write the JuMP model `model` to `filename` in the format `format`.

If the filename ends in `.gz`, it will be compressed using Gzip. If the filename ends in `.bz2`, it will be compressed using BZip2.

Other `kwargs` are passed to the `Model` constructor of the chosen format.
