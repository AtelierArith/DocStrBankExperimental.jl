```julia
solve!(
    model::PowerSimulations.DecisionModel;
    export_problem_results,
    console_level,
    file_level,
    disable_timer_outputs,
    export_optimization_problem,
    kwargs...
) -> InfrastructureSystems.Simulation.RunStatusModule.RunStatus

```

Default solve method for models that conform to the requirements of DecisionModel{<: DecisionProblem}.

This will call `build!` on the model if it is not already built. It will forward all keyword arguments to that function.

# Arguments

  * `model::OperationModel = model`: operation model
  * `export_problem_results::Bool = false`: If true, export OptimizationProblemResults DataFrames to CSV files. Reduces solution times during simulation.
  * `console_level = Logging.Error`:
  * `file_level = Logging.Info`:
  * `disable_timer_outputs = false` : Enable/Disable timing outputs
  * `export_optimization_problem::Bool = true`: If true, serialize the model to a file to allow re-execution later.

# Examples

```julia
results = solve!(OpModel)
results = solve!(OpModel, export_problem_results = true)
```
