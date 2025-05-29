```
PackageIndex(modules; kwargs...)
```

Index the packages that define `modules`. The created index contains tables of the following data associated with the packages:

  * packages
  * modules
  * symbols
  * methods
  * docstrings
  * source files
  * bindings

## Keyword arguments

  * `cache = false`: Cache to use to store the index. If `true`, use the default, global   file-based cache (`ModuleInfo.CACHE[]`). You can also pass a [`InfoCache`](#) directly.   If a cache is used, already indexed packages will not be reindexed. In-development   packages *will* be reindexed if they have changed since the cache was built.
  * `verbose = false`: If `true`, print which package is being indexed while running.
  * `packages = nothing`: Pass a `Vector{String}` to limit which packages are indexed to those   specified. Useful when using the `recurse` option and you only want to index some   dependencies.
  * `recurse = 0`: How many levels to recurse into `packages`' dependencies. The default `0`   means no dependencies are indexed. `1` would mean that only direct dependencies   of every package in `packages` are indexed.
  * `pkgtags = Dict{String, String}()`: A mapping of `package_name => version_name` that can   be used to overwrite the version that a package will be saved as.

## Examples

Index a package:

{cell}

```julia
using ModuleInfo
pkgindex = PackageIndex([ModuleInfo])
```

Index a package and its direct dependencies:

{cell}

```julia
using ModuleInfo
pkgindex = PackageIndex([ModuleInfo], recurse = 1)
ModuleInfo.getid.(pkgindex.packages)
```
