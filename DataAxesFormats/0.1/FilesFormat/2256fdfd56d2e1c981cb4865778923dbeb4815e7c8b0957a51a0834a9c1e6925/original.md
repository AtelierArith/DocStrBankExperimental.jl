```
FilesDaf(
    path::AbstractString,
    mode::AbstractString = "r";
    [name::Maybe{AbstractString} = nothing]
)
```

Storage in disk files in some directory.

When opening an existing data set, if `name` is not specified, and there exists a "name" scalar property, it is used as the name. Otherwise, the `path` will be used as the name.

The valid `mode` values are as follows (the default mode is `r`):

| Mode | Allow modifications? | Create if does not exist? | Truncate if exists? | Returned type         |
|:---- |:-------------------- |:------------------------- |:------------------- |:--------------------- |
| `r`  | No                   | No                        | No                  | [`DafReadOnly`](@ref) |
| `r+` | Yes                  | No                        | No                  | [`FilesDaf`](@ref)    |
| `w+` | Yes                  | Yes                       | No                  | [`FilesDaf`](@ref)    |
| `w`  | Yes                  | Yes                       | Yes                 | [`FilesDaf`](@ref)    |
