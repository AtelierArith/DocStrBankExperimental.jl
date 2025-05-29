```
Experiment
```

The structure used to embody a reproduce experiment. This is usually constructed through the [`parse_experiment_from_config`](@ref), but can be used without config files.

  * `dir`: the base directory of the experiment (where the info files are saved).
  * `file`: The file containing the experiment function described by `func_name` and `module_name`
  * `module_name`: Module name containing the experiment function.
  * `func_name`: Function name of the experiment.
  * `save_type`: The save structure to deal with saving data passed by the experiment.
  * `args_iter`: The args iterator which contains the configs to pass to the experiment.
  * `[confg]`: The config file parsed to create the experiment (optional)

# kwarg

  * `[comp_env]`: The computational environment used by the experiment.
