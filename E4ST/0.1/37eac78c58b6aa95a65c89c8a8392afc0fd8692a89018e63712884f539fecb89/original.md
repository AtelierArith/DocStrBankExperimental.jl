```
process_results!(config::OrderedDict, data::OrderedDict) -> data
```

Calls [`modify_results!(mod, config, data)`](@ref) for each `Modification` in `config`.  Stores the results into `get_out_path(config, "data_processed.jls")` if `config[:save_data_processed]` is `true` (default).
