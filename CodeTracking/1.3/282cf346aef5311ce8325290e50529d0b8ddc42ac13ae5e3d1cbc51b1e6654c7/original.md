```
info = pkgfiles(mod::Module)
```

Return a [`CodeTracking.PkgFiles`](@ref) structure with information about the files that were loaded to define the package that defined `mod`.
