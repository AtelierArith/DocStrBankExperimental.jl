```
process_results!(mod_file::String, out_path::String; processed=true) -> data
```

Processes the results the [`Modification`](@ref)s found in `mod_file`, a .yml file similar to a `config` file (see [`read_config`](@ref)), only requiring the `mods` field.

  * `processed=false` - reads in `data` via [`read_parsed_results`](@ref)
  * `processed=true` - reads in `data` via [`read_processed_results`](@ref)
