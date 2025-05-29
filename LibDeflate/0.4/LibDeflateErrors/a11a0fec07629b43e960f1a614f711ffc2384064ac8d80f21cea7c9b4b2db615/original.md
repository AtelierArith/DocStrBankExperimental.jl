```
LibDeflateError
```

A `UInt8` enum representing that LibDeflate encountered an error. The numerical value of the errors are not stable across non-breaking releases, but their names are. Code checking for specific errors should check by e.g. `== LibDeflateErrors.gzip_not_deflate`. Successful operations will never return a `LibDeflateError`.
