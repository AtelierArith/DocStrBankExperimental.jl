```
localmodels(; modl=Main, wrappers=false)
localmodels(filters...; modl=Main, wrappers=false)
localmodels(needle::Union{AbstractString,Regex}; modl=Main, wrappers=false)
```

List all models currently available to the user from the module `modl` without importing a package, and which additional pass through the specified filters. Here a *filter* is a `Bool`-valued function on models.

Use `load_path` to get the path to some model returned, as in these examples:

```
ms = localmodels()
model = ms[1]
load_path(model)
```

See also [`models`](@ref), [`load_path`](@ref).
