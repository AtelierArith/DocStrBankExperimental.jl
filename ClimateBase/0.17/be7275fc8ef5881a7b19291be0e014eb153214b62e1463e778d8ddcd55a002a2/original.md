```
ncwrite(file::String, Xs; globalattr = Dict())
```

Write the given `ClimArray` instances (any iterable of `ClimArray`s or a single `ClimArray`) to a `.nc` file following CF standard conventions using NCDatasets.jl. Optionally specify global attributes for the `.nc` file.

The metadata of the arrays in `Xs`, as well as their dimensions, are properly written in the `.nc` file and any necessary type convertions happen automatically.

**WARNING**: We assume that any dimensions shared between the `Xs` are identical.

See also [`ncread`](@ref).
