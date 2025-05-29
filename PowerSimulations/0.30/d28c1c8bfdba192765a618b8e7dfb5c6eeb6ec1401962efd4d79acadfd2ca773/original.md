```julia
run!(
    model::PowerSimulations.EmulationModel;
    export_problem_results,
    console_level,
    file_level,
    disable_timer_outputs,
    export_optimization_model,
    kwargs...
) -> InfrastructureSystems.Simulation.RunStatusModule.RunStatus

```

Default run method for problems that conform to the requirements of EmulationModel{<: EmulationProblem}

This will call `build!` on the model if it is not already built. It will forward all keyword arguments to that function.

# Arguments

  * `model::EmulationModel = model`: Emulation model
  * `optimizer::MOI.OptimizerWithAttributes`: The optimizer that is used to solve the model
  * `executions::Int`: Number of executions for the emulator run
  * `export_problem_results::Bool`: If true, export OptimizationProblemResults DataFrames to CSV files.
  * `output_dir::String`: Required if the model is not already built, otherwise ignored
  * `enable_progress_bar::Bool`: Enables/Disable progress bar printing
  * `export_optimization_model::Bool`: If true, serialize the model to a file to allow re-execution later.

# Examples

```julia
status = run!(model; optimizer = HiGHS.Optimizer, executions = 10)
status = run!(model; output_dir = ./model_output, optimizer = HiGHS.Optimizer, executions = 10)
```
