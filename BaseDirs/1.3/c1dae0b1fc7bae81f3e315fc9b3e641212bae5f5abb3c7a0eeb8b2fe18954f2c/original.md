```
config(; create, existent) -> Vector{String} # all user and system configuration directories
config([mod::Module or proj::Project], parts...; create, existent) # a [project-specific] user and system configuration path
```

Locate all user and system configuration directories, or a path within it.

A project or module can be optionally provided as the first argument, in which case the returned path is scoped to the project or module.

The returned path is determined by the value of [`BaseDirs.CONFIG_HOME`](@ref), and [`BaseDirs.CONFIG_DIRS`](@ref), which see.

## Keyword arguments

  * `create::Bool` (default `false`), whether the path should be created if it does not exist. Paths ending in `/` are interpreted as directories, and all other paths are considered files. This takes care to create the base directories with the appropriate permissions (700).
  * `existent::Bool` (default `false`), filter out paths that do not exist.
