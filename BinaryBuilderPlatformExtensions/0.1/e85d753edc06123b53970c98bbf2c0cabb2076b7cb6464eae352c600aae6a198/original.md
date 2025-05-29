```
macos_version(p::AbstractPlatform)
```

If no `os_version` is specified in `p`, default to the oldest we support in the Julia world, which is `macOS 10.8` (kernel version 14), but if it is actually specified, then return the specified value (mapping from kernel version to macOS version).

```jldoctest
julia> macos_version(Platform("x86_64", "macos"; os_version="18"))
"10.14"
```
