```
FileProduct(path, varname::Symbol, dir_path = nothing)
```

Declares a [`FileProduct`](@ref) that points to a file located relative to the root of a `Prefix`, must simply exist to be satisfied. The first argument `path` is either a single `AbstractString`  or a `Vector{String}` to allow several paths to be checked.   
