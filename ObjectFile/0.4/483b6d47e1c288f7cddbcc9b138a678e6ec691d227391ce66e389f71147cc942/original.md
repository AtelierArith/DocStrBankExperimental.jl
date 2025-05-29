```
find_libraries(oh::ObjectHandle)
```

Return a mapping from sonames to absolute paths, containing all the sonames declared as beeing needed by the given `ObjectHandle`.  See the documentation for `find_library(::RPath, ::String)` and `RPath` for more details.
