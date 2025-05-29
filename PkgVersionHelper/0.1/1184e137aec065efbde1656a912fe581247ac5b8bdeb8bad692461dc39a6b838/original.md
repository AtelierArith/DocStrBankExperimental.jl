```
upcheck(; indirect_deps=false)
```

Checks which package is not up to date. It wil return a `Dict{String, Tuple{VersionNumber, VersionNumber}}` with these key-value paiars

```
`PkgName => (installed_version, latest_version)`
```

Keyword argument `indirect_deps` if `true` includes the indirect dependencies.
