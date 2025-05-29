```
PostprocessCallback(; interval::Integer=0, dt=0.0, exclude_boundary=true, filename="values",
                    output_directory="out", append_timestamp=false, write_csv=true,
                    write_json=true, write_file_interval=1, funcs...)
```

Create a callback to post-process simulation data at regular intervals. This callback allows for the execution of a user-defined function `func` at specified intervals during the simulation. The function is applied to the current state of the simulation, and its results can be saved or used for further analysis. The provided function cannot be anonymous as the function name will be used as part of the name of the value.

The callback can be triggered either by a fixed number of time steps (`interval`) or by a fixed interval of simulation time (`dt`).

# Keywords

  * `funcs...`:   Functions to be executed at specified intervals during the simulation.               Each function must have the arguments `(system, data, t)`,               which will be called for every system, where `data` is a named               tuple with fields depending on the system type, and `t` is the               current simulation time. Check the available data for each               system with `available_data(system)`.               See [Custom Quantities](@ref custom_quantities)               for a list of pre-defined custom quantities that can be used here.
  * `interval=0`: Specifies the number of time steps between each invocation of the callback.               If set to `0`, the callback will not be triggered based on time steps.               Either `interval` or `dt` must be set to something larger than 0.
  * `dt=0.0`: Specifies the simulation time interval between each invocation of the callback.           If set to `0.0`, the callback will not be triggered based on simulation time.           Either `interval` or `dt` must be set to something larger than 0.
  * `exclude_boundary=true`: If set to `true`, boundary particles will be excluded from the post-processing.
  * `filename="values"`: The filename of the postprocessing files to be saved.
  * `output_directory="out"`: The path where the results of the post-processing will be saved.
  * `write_csv=true`: If set to `true`, write a csv file.
  * `write_json=true`: If set to `true`, write a json file.
  * `append_timestep=false`: If set to `true`, the current timestamp will be added to the filename.
  * `write_file_interval=1`: Files will be written after every `write_file_interval` number of                          postprocessing execution steps. A value of 0 indicates that files                          are only written at the end of the simulation, eliminating I/O overhead.

# Examples

```jldoctest; output = false
# Create a callback that is triggered every 100 time steps
postprocess_callback = PostprocessCallback(interval=100, example_quantity=kinetic_energy)

# Create a callback that is triggered every 0.1 simulation time units
postprocess_callback = PostprocessCallback(dt=0.1, example_quantity=kinetic_energy)

# output
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ PostprocessCallback                                                                              │
│ ═══════════════════                                                                              │
│ dt: ……………………………………………………………………… 0.1                                                              │
│ write file: ………………………………………………… always                                                           │
│ exclude boundary: ………………………………… yes                                                              │
│ filename: ……………………………………………………… values                                                           │
│ output directory: ………………………………… out                                                              │
│ append timestamp: ………………………………… no                                                               │
│ write json file: …………………………………… yes                                                              │
│ write csv file: ……………………………………… yes                                                              │
│ function1: …………………………………………………… example_quantity                                                 │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
