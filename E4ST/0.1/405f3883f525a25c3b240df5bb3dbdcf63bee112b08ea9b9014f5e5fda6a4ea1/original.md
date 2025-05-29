```
extract_results(post_config) -> post_data::OrderedDict{Symbol, Any}
```

Initializes `post_data`, and extracts results for each modification in `post_config[:mods]`, for each of the simulations in `post_config[:sim_paths]` and `post_config[:sim_names]`.  

Calls `extract_results(post_mod, config, data)` for each `post_mod`, where `config` is the simulation config, and `data` is the simulation data, read in from `read_processed_results`.
