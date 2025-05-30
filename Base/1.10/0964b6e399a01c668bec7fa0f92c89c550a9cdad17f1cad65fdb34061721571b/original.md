```
include_dependency(path::AbstractString)
```

In a module, declare that the file, directory, or symbolic link specified by `path` (relative or absolute) is a dependency for precompilation; that is, the module will need to be recompiled if the modification time of `path` changes.

This is only needed if your module depends on a path that is not used via [`include`](@ref). It has no effect outside of compilation.
