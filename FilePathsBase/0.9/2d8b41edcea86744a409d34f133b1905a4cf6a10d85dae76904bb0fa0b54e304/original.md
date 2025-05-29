```
sync([f::Function,] src::AbstractPath, dst::AbstractPath; delete=false, overwrite=true)
```

Recursively copy new and updated files from the source path to the destination. If delete is true then files at the destination that don't exist at the source will be removed. By default, source files are sent to the destination if they have different sizes or the source has newer last modified date.

Optionally, you can specify a function `f` which will take a `src` and `dst` path and return true if the `src` should be sent. This may be useful if you'd like to use a checksum for comparison.
