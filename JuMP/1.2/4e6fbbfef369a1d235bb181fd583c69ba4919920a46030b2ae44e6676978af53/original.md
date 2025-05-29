```
read_from_file(
    filename::String;
    format::MOI.FileFormats.FileFormat = MOI.FileFormats.FORMAT_AUTOMATIC,
    kwargs...,
)
```

Return a JuMP model read from `filename` in the format `format`.

If the filename ends in `.gz`, it will be uncompressed using Gzip. If the filename ends in `.bz2`, it will be uncompressed using BZip2.

Other `kwargs` are passed to the `Model` constructor of the chosen format.
