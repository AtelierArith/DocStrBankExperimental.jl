```
explore(sim_inst::SimulationInstance; title="Electron", model_index::Int = 1, scen_name::Union{Nothing, String} = nothing, results_output_dir::Union{Nothing, String} = nothing)
```

Produce a UI to explore the output distributions of the saved variables in `SimulationInstance` `sim` for results of model `model_index` and scenario with the name `scen_name` in a Window with title `title`. The optional arguments default to a `model_index` of `1`, a `scen_name` of `nothing`  assuming there is no secenario dimension, and a window with title `Electron`.   The `results_output_dir` keyword argument refers to the main output directory as provided to `run`,  where all subdirectories are held. If provided, results are assumed to be stored there, otherwise it is  assumed that results are held in results.sim and not  in an output folder.
