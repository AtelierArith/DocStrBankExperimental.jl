```
info = pkgfiles(name::AbstractString)
info = pkgfiles(name::AbstractString, uuid::UUID)
```

Return a [`CodeTracking.PkgFiles`](@ref) structure with information about the files that define the package specified by `name` and `uuid`. Returns `nothing` if this package has not been loaded.
