```
simulate_data_file(inp; parse_arg = NamedTuple(), kwarg...)
```

Simulate standard input file (with extension .DATA). `inp` can either be the output from the GeoEnergyIO function `parse_data_file` or a `String` for the path of an input file with the .DATA extension.

Additional arguments are passed onto [`simulate_reservoir`](@ref). Extra inputs to the parser can be sent as a `setup_arg` `NamedTuple`.
