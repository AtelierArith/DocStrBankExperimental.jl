```
expand_cxxstring_abis(p::AbstractPlatform; skip=Sys.isbsd)
```

Given a `Platform`, returns an array of `Platforms` with a spread of identical entries with the exception of the `cxxstring_abi` tag within the `Platform` object.  This is used to take, for example, a list of supported platforms and expand them to include multiple GCC versions for the purposes of ABI matching.

If the given `Platform` already specifies a `cxxstring_abi` (as opposed to `nothing`) only that `Platform` is returned.  If `skip` is a function for which `skip(platform)` evaluates to `true`, the given platform is not expanded.  By default FreeBSD and macOS platforms are skipped, due to their lack of a dependence on `libstdc++` and not needing this compatibility shim.
