```julia
System(
    file_path::AbstractString;
    assign_new_uuids,
    try_reimport,
    kwargs...
) -> Any

```

Constructs a System from a file path ending with .m, .raw, or .json

If the file is JSON, then `assign_new_uuids = true` will generate new UUIDs for the system and all components. If the file is .raw, then `try_reimport = false` will skip searching for a `<name>_export_metadata.json` file in the same directory.
