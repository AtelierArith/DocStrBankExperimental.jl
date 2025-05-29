```
find_library(oh::ObjectHandle, soname::String)
```

Return the absolute path to the given `soname`, using the linker search path that the given `ObjectHandle` would use at runtime.  See the documentation for `find_library(::RPath, ::String)` for more details.
