```
struct FilePath path::String end
```

Crude stand in for a file path type, which is strangely absent from Base.

This allows for load/write method dispatch, and the distinguishing of file content (as a String) from file paths.

# Examples

```julia-repl
julia> string(FilePath("some/path"))
"some/path"
```
