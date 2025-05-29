```
locate(ep::ExecutableProduct, prefix::String;
       verbose::Bool = false)
```

If the given executable file exists and is executable, return its path.

On all platforms, an [`ExecutableProduct`](@ref) checks for existence of the file.  On non-Windows platforms, it will check for the executable bit being set. On Windows platforms, it will check that the file ends with ".exe", (adding it on automatically, if it is not already present).
