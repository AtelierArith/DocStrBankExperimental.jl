```
supported_platforms(;exclude::Union{Vector{<:Platform},Function}=Returns(false),
                    experimental::Bool=false)
```

Return the list of supported platforms as an array of `Platform`s.  These are the platforms we officially support building for, if you see a mapping in `get_shard_hash()` that isn't represented here, it's probably because that platform is still considered "in beta".  If `experimental=true`, include platforms considered experimental.

Platforms can be excluded from the list by specifying an array of platforms to `exclude` i.e. `supported_platforms(exclude=[Platform("i686", "windows"), Platform("x86_64", "windows")])` or a function that returns true for exclusions i.e.

```
supported_platforms(exclude=Sys.islinux)
```
