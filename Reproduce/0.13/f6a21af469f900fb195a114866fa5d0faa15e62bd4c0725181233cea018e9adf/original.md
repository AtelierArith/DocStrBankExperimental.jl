```
pre_experiment(exp::Experiment; kwargs...)
pre_experiment(file_save::FileSave, exp; kwargs...)
pre_experiment(sql_save::SQLSave, exp; kwargs...)
```

This function does all the setup required to successfully run an experiment. It is dispatched on the save structure in the experiment.

This function:

  * Creates the base experiment directory.
  * Runs [`experiment_save_init`](@ref) to initialize the details for each save type.
  * runs [`add_experiment`](@ref)
