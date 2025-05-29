```julia
generate_struct_file(
    definition::InfrastructureSystems.StructDefinition;
    filename,
    output_directory
)

```

Generate a Julia source code file for one struct from a `StructDefinition`.

Refer to `StructDefinition` and `StructField` for descriptions of the available fields.

# Arguments

  * `definition::StructDefinition`: Defines the struct and all fields.
  * `filename::AbstractString`: Add the struct definition to this JSON file. Defaults to `src/descriptors/power_system_structs.json`
  * `output_directory::AbstractString`: Generate the files in this directory. Defaults to `src/models/generated`
