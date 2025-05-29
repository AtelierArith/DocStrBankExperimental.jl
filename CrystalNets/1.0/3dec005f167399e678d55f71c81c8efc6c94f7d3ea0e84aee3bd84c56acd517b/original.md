```
parse_cgd(path::AbstractString; strict=true)
```

Parse a .cgd Systre configuration data file such as the one used by the RCSR. Return a list of `id => g` where `id` is the name of the structure and `g` is its `PeriodicGraph`.

If `strict` is set, refuse structures that seem to contain errors (inconsistent connectivity, missing cell, incorrect number of vertices) and print an `@error` instead.
