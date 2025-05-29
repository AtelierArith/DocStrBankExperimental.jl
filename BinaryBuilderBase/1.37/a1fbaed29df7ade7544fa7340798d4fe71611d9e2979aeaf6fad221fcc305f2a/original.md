```
expand_gfortran_versions(p::AbstractPlatform)
```

Given a `Platform`, returns an array of `Platforms` with a spread of identical entries with the exception of the `libgfortran_version` tag within the `Platform`.  This is used to take, for example, a list of supported platforms and expand them to include multiple GCC versions for the purposes of ABI matching.  If the given `Platform` already specifies a `libgfortran_version` (as opposed to `nothing`) only that `Platform` is returned.
