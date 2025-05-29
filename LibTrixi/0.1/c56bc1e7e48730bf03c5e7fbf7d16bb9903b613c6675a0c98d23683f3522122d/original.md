```
trixi_version_julia()::Cstring
```

Return name and version of loaded Julia packages LibTrixi directly depends on.

The return value is a read-only pointer to a NULL-terminated string with the name and version information of the loaded Julia packages, separated by newlines.

The returned pointer is to static memory and must not be used to change the contents of the version string. Multiple calls to the function will return the same address.

This function is thread-safe. It must be run after `trixi_initialize` has been called.
