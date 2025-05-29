```
ExecutableProduct(names::Vector{String}, varname::Symbol; dir_path = nothing)
```

On all platforms, an `ExecutableProduct` checks for existence of the file.  On Windows platforms, it will check that the file ends with ".exe", (adding it on automatically to the search paths, if it is not already present).
