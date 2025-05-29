```
find_library(rpath::RPath, soname::String)
```

Return the full path to a library, searching the given `RPath`, and then the default library search paths.  This method takes the given `soname` and joins it to the end of every path within the given `RPath`, returning the resultant path if it exists, returning back the original `soname` if it doesn't.
