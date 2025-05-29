```
load!(filename::AbstractString, x)
```

Load an object stored in a JLD2 file at `filename` and copy its contents to `x`.

Note: To `load!` in MPI mode, use [`pload!`](@ref).
