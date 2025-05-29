```
run_e4st(config) -> out_path

run_e4st(filename(s)) -> out_path
```

Top-level function for running E4ST.  Here is a general overview of what happens:

1. Book-keeping

      * [`read_config(config_file)`](@ref) - loads in the `config` from file, if not passed in directly.
      * [`save_config(config)`](@ref) - the config is saved to `config[:out_path]`
      * [`start_logging!(config)`](@ref) - Logging is started, some basic information is logged via [`log_start`](@ref).
2. Load Input Data

      * [`read_data(config)`](@ref) - The data is loaded in from files specified in the `config`.
3. Construct JuMP Model and optimize

      * [`setup_model(config, data)`](@ref) - The `model` (a JuMP Model) is set up.
      * [`JuMP.optimize!(model)`](https://jump.dev/JuMP.jl/stable/reference/solutions/#JuMP.optimize!) - The `model` is optimized.
4. Process Results

      * [`parse_results!(config, data, model)`](@ref) - Retrieves all necessary values and shadow prices from `model`, storing them into data[:results][:raw], (see [`get_raw_results`](@ref) and [`get_results`](@ref)) and saves `data` if `config[:save_data_parsed]` is `true` (default is `true`).  This is mostly stored in case the results processing throws an error before completion.  That way, there is no need to re-run the model.
      * [`process_results!(config, data)`](@ref) - Calls [`modify_results!(mod, config, data)`](@ref) for each `mod` in the `config`. Saves `data` if `config[:save_data_processeded]` is `true` (default is `true`)
5. Iterate, running more simulations as needed.

      * See [`Iterable`](@ref) and [`read_config`](@ref) for more information.
