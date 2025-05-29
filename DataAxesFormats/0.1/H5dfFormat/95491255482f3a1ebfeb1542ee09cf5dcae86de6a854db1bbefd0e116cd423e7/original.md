```
H5df(
    root::Union{AbstractString, HDF5.File, HDF5.Group},
    mode::AbstractString = "r";
    [name::Maybe{AbstractString} = nothing]
)
```

Storage in a HDF5 file.

The `root` can be the path of an HDF5 file, which will be opened with the specified `mode`, or an opened HDF5 file, in which cases the `Daf` data set will be stored directly in the root of the file (by convention, using a `.h5df` file name suffix). Alternatively, the `root` can be a group inside an HDF5 file, which allows to store multiple `Daf` data sets inside the same HDF5 file (by convention, using a `.h5dfs` file name suffix).

When opening an existing data set, if `name` is not specified, and there exists a "name" scalar property, it is used as the name. Otherwise, the path of the HDF5 file will be used as the name, followed by the internal path of the group (if any).

The valid `mode` values are as follows (the default mode is `r`):

| Mode | Allow modifications? | Create if does not exist? | Truncate if exists? | Returned type         |
|:---- |:-------------------- |:------------------------- |:------------------- |:--------------------- |
| `r`  | No                   | No                        | No                  | [`DafReadOnly`](@ref) |
| `r+` | Yes                  | No                        | No                  | [`H5df`](@ref)        |
| `w+` | Yes                  | Yes                       | No                  | [`H5df`](@ref)        |
| `w`  | Yes                  | Yes                       | Yes                 | [`H5df`](@ref)        |

!!! note
    If specifying a path (string) `root`, when calling `h5open`, the file alignment of created files is set to `(1, 8)` to maximize efficiency of mapped vectors and matrices, and the `w+` mode is converted to `cw`.

