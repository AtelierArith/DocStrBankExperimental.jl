```julia
setlogger(path, name; setglobal, loglevel)

```

Returns a logger. `path` is the path and `name` is the name of the file of the logger. If `setglobal` is `true`, the returned logger is a global logger.

# Example

```julia
julia> logger = setlogger(tempdir(), "mylogger", setglobal=true)
Base.CoreLogging.SimpleLogger(IOStream(<file /tmp/mylogger>), Info, Dict{Any,Int64}())
```
