```
read_data(config) -> data
```

Pulls in data found in files listed in the `config`, and stores into `data`.

Calls the following functions:

  * [`read_data_files!(config, data)`](@ref) - read in the data from files
  * [`modify_raw_data!(config, data)`](@ref) - Gives [`Modification`](@ref)s a chance to modify the raw data before the data gets setup.
  * [`setup_data!(config, data)`](@ref) - Sets up the data, modifying/adding to the tables as needed.
  * [`modify_setup_data!(config, data)`](@ref) - Gives [`Modification`](@ref)s a chance to modify the setup data before the model is built.
