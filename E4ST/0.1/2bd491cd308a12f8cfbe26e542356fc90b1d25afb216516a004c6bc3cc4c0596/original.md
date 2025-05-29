```
parse_results!(config, data, model) -> nothing
```

  * Gathers the values and shadow prices of each variable, expression, and constraint stored in the model and dumps them into `data[:results][:raw]` (see [`get_raw_results`](@ref) and [`get_results`](@ref)).
  * Adds relevant info to `gen`, `bus`, and `branch` tables.  See [`parse_lmp_results!`](@ref) and [`parse_power_results!`](@ref) for more information.
  * Saves updated `gen` table via [`save_updated_gen_table`](@ref)
  * Saves `data` to `get_out_path(config,"data_parsed.jls")` unless `config[:save_data_parsed]` is `false` (true by default).
