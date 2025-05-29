```
dispatch_setup(model, attribute_name, modeldata, cellranges=modeldata.cellranges_all)
```

Call setup methods, eg to initialize data arrays (including state variables).

`attribute_name` defines the setup operation performed. `dispatch_setup` should be called in sequence with `attribute_name` = :

  * `:setup`: initialise Reactions and set up any non-state Variables (eg model grid Variables) (applied to `modeldata` `arrays_idx=1`, values then copied to other `arrays_idx`)
  * `:norm_value`: set state Variable values from `:norm_value` attribute in .yaml file, and initialise any Reaction state that requires this value (`arrays_idx` 1 only)
  * `:initial_value` (optional): set state Variable values from `:initial_value` attribute in .yaml file (`arrays_idx` 1 only)
