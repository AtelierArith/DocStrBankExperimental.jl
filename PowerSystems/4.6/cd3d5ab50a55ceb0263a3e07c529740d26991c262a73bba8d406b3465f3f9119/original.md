```julia
generate_struct_files(
    definitions;
    filename,
    output_directory
)

```

Generate Julia source code files for multiple structs from a iterable of `StructDefinition` instances.

Refer to `StructDefinition` and `StructField` for descriptions of the available fields.

# Arguments

  * `definitions`: Defines the structs and all fields.
  * `filename::AbstractString`: Add the struct definition to this JSON file. Defaults to `src/descriptors/power_system_structs.json`
  * `output_directory::AbstractString`: Generate the files in this directory. Defaults to `src/models/generated`
