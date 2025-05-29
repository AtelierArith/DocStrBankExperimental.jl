```
cache(; create) -> String # the cached data directory
cache([mod::Module or proj::Project], parts...; create) # a [project-specific] cached data path
```

Locate the cached data directory, or a path within it.

A project or module can be optionally provided as the first argument, in which case the returned path is scoped to the project or module.

The returned path is determined by the value of [`BaseDirs.CACHE_HOME`](@ref), which see.

## Keyword arguments

  * `create::Bool` (default `false`), whether the path should be created if it does not exist. Paths ending in `/` are interpreted as directories, and all other paths are considered files. This takes care to create the base directories with the appropriate permissions (700).
