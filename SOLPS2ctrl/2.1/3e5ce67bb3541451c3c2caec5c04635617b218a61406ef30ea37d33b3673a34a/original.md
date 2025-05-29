```
find_files_in_allowed_folders(
    input_dirs::String...;
    eqdsk_file::String,
    recursive::Bool=true,
)
```

Searches a list of allowed folders for a set of filenames that will provide information about the SOLPS case. Returns a list of filenames with complete paths.

Example:

```julia
SOLPS2ctrl.find_files_in_allowed_folders(
    "<your samples folder>/D3D_Ma_184833_03600";
    eqdsk_file="g184833.03600",
)
```
