```
AbstractPath
```

Defines an abstract filesystem path.

# Properties

  * `segments::Tuple{Vararg{String}}` - path segments (required)
  * `root::String` - path root (defaults to "/")
  * `drive::String` - path drive (defaults to "")
  * `separator::String` - path separator (defaults to "/")

# Required Methods

  * `tryparse(::Type{T}, str::String)` - For parsing string representations of your path
  * `read(path::T)`
  * `write(path::T, data)`
  * `exists(path::T` - whether the path exists
  * `stat(path::T)` - File status describing permissions, size and creation/modified times
  * `mkdir(path::T; kwargs...)` - Create a new directory
  * `rm(path::T; kwags...)` - Remove a file or directory
  * `readdir(path::T)` - Scan all files and directories at a specific path level
