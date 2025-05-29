```
trixi_version_julia_extended()::Cstring
```

Return name and version of all loaded Julia packages.

The return value is a read-only pointer to a NULL-terminated string with the name and version information of all loaded Julia packages, including implicit dependencies, separated by newlines.

The returned pointer is to static memory and must not be used to change the contents of the version string. Multiple calls to the function will return the same address.

This function is thread-safe. It must be run after `trixi_initialize` has been called.
