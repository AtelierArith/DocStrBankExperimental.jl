```
SolutionSavingCallback(; interval::Integer=0, dt=0.0, save_times=Array{Float64, 1}([]),
                       save_initial_solution=true, save_final_solution=true,
                       output_directory="out", append_timestamp=false, prefix="",
                       verbose=false, write_meta_data=true, max_coordinates=2^15,
                       custom_quantities...)
```

Callback to save the current numerical solution in VTK format in regular intervals. Either pass `interval` to save every `interval` time steps, or pass `dt` to save in intervals of `dt` in terms of integration time by adding additional `tstops` (note that this may change the solution).

Additional user-defined quantities can be saved by passing functions as keyword arguments, which map `(v, u, t, system)` to an `Array` where the columns represent the particles in the same order as in `u`. To ignore a custom quantity for a specific system, return `nothing`.

# Keywords

  * `interval=0`:                 Save the solution every `interval` time steps.
  * `dt`:                         Save the solution in regular intervals of `dt` in terms                               of integration time by adding additional `tstops`                               (note that this may change the solution).
  * `save_times=[]`               List of times at which to save a solution.
  * `save_initial_solution=true`: Save the initial solution.
  * `save_final_solution=true`:   Save the final solution.
  * `output_directory="out"`:     Directory to save the VTK files.
  * `append_timestamp=false`:     Append current timestamp to the output directory.
  * 'prefix=""':                  Prefix added to the filename.
  * `custom_quantities...`:       Additional user-defined quantities.
  * `write_meta_data=true`:       Write meta data.
  * `verbose=false`:              Print to standard IO when a file is written.
  * `max_coordinates=2^15`:       The coordinates of particles will be clipped if their                               absolute values exceed this threshold.
  * `custom_quantities...`:   Additional custom quantities to include in the VTK output.                           Each custom quantity must be a function of `(system, data, t)`,                           which will be called for every system, where `data` is a named                           tuple with fields depending on the system type, and `t` is the                           current simulation time. Check the available data for each                           system with `available_data(system)`.                           See [Custom Quantities](@ref custom_quantities)                           for a list of pre-defined custom quantities that can be used here.

# Examples

```jldoctest; output = false, filter = [r"output directory:.*", r"\s+│"]
# Save every 100 time steps
saving_callback = SolutionSavingCallback(interval=100)

# Save in intervals of 0.1 in terms of simulation time
saving_callback = SolutionSavingCallback(dt=0.1)

# Additionally store the kinetic energy of each system as "my_custom_quantity"
saving_callback = SolutionSavingCallback(dt=0.1, my_custom_quantity=kinetic_energy)

# output
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ SolutionSavingCallback                                                                           │
│ ══════════════════════                                                                           │
│ dt: ……………………………………………………………………… 0.1                                                              │
│ custom quantities: ……………………………… [:my_custom_quantity => TrixiParticles.kinetic_energy]           │
│ save initial solution: …………………… yes                                                              │
│ save final solution: ………………………… yes                                                              │
│ output directory: ………………………………… *path ignored with filter regex above*                           │
│ prefix: ……………………………………………………………                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
