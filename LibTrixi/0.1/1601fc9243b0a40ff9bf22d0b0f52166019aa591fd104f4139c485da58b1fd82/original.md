```
trixi_version_library()::Cstring
```

Return full version string of libtrixi.

The return value is a read-only pointer to a NULL-terminated string with the version information. This may include not just MAJOR.MINOR.PATCH but possibly also additional build or development version information.

The returned pointer is to static memory and must not be used to change the contents of the version string. Multiple calls to the function will return the same address.

This function is thread-safe. It must be run after `trixi_initialize` has been called.
