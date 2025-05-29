```julia
struct Postprocess
```

Contains postprocessing options for a given simulation. When `run_simulation(config, sim_params; postprocess = Postprocess(...))` is called with a non-empty `output_file`, `HallThruster` will write the simulation results to a JSON file. The results in the file will be transformed according to the fields.

## Fields

  * `output_file::String`: The file to which the output will be written. If empty, no output will be written.

  * `average_start_time::Float64`: The time to begin averaging at. If less than zero, no averaged output will be written.

  * `save_time_resolved::Bool`: Whether time-resolved output will be saved. If true, each frame of the simulation will be written to the output file.
