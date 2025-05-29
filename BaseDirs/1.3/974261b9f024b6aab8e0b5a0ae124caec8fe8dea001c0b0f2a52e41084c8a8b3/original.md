```
applications(; create, existent) -> Vector{String} # all user and system applications directories
applications([mod::Module or proj::Project], parts...; create, existent) # a [project-specific] user and system applications path
```

Locate all user and system applications directories, or a path within it.

A project or module can be optionally provided as the first argument, in which case the returned path is scoped to the project or module.

## Keyword arguments

  * `create::Bool` (default `false`), whether the path should be created if it does not exist. Paths ending in `/` are interpreted as directories, and all other paths are considered files. This takes care to create the base directories with the appropriate permissions (700).
  * `existent::Bool` (default `false`), filter out paths that do not exist.
