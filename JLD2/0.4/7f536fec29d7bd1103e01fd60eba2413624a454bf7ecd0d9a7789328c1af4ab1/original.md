```
jldopen(fname::AbstractString, mode::AbstractString;
        iotype=MmapIO, compress=false, typemap=Dict())
```

Opens a JLD2 file at path `fname`.

Options for `mode`:

  * `"r"`: Open for reading only, failing if no file exists
  * `"r+"`: Open for reading and writing, failing if no file exists
  * `"w"`/`"w+"`: Open for reading and writing, overwriting the file if it already exists
  * `"a"`/`"a+"`: Open for reading and writing, creating a new file if none exists, but               preserving the existing file if one is present
