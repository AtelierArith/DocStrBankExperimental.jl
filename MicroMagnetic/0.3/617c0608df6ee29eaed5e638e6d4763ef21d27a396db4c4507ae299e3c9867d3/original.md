```
sim_with(args::Union{NamedTuple, Dict})
```

[High-Level Interface](@ref) for starting a typical micromagnetic simulation. All parameters are set using `args`, which can be either a `NamedTuple` or a `Dict`.

# Keywords

  * `mesh`: A mesh must be provided to start the simulation. The mesh could be [`FDMesh`](@ref), [`CubicMesh`](@ref), or [`TriangularMesh`](@ref).
  * `name`: The name of the simulation, provided as a string.
  * `task`: The type of simulation task, which can be `"Relax"` or `"Dynamics"`. The default is "Relax".
  * `driver`: The name of the driver, which should be "SD", "LLG", or "LLG_STT". The default is "SD".
  * `alpha`: The Gilbert damping parameter in the LLG equation, provided as a number.
  * `beta`: The nonadiabatic strength in the LLG equation with spin-transfer torques (Zhang-Li model), provided as a number.
  * `gamma`: The gyromagnetic ratio, with a default value of 2.21e5.
  * `ux`, `uy`, `uz`: The components of the spin-transfer torque strength.
  * `ufun`: A time-dependent function for `u`.
  * `Ms`: The saturation magnetization, which should be a [`NumberOrArrayOrFunction`](@ref). The default is `Ms=8e5`.
  * `mu_s`: The magnetic moment, which should be a [`NumberOrArrayOrFunction`](@ref). The default is `mu_s=2*mu_B`.
  * `A` or `J`: The exchange constant, which should be a [`NumberOrArrayOrFunction`](@ref).
  * `D`: The Dzyaloshinskii-Moriya interaction (DMI) constant, which should be a [`NumberOrArrayOrFunction`](@ref).
  * `dmi_type`: The type of DMI, either "bulk" or "interfacial".
  * `Ku`: The anisotropy constant, which should be a [`NumberOrArrayOrFunction`](@ref).
  * `axis`: The anisotropy axis, provided as a tuple, e.g., `(0, 0, 1)`.
  * `Kc`: the cubic anisotropy constant, should be [`NumberOrArrayOrFunction`](@ref).
  * `axis1`: the cubic anisotropy axis1, should be a tuple, such as (1,0,0)
  * `axis2`: the cubic anisotropy axis2, should be a tuple, such as (0,1,0)
  * `demag`: Whether to include demagnetization. This should be a boolean (`true` or `false`). The default is `demag=false`.
  * `H`: The external magnetic field, which should be a tuple or function, i.e., [`TupleOrArrayOrFunction`](@ref).
  * `m0`: The initial magnetization, which should be a tuple or function, i.e., [`TupleOrArrayOrFunction`](@ref).
  * `T`: The temperature, which should be a [`NumberOrArrayOrFunction`](@ref).
  * `shape`: The shape defines the geometry of the sample, where parameters are configured.
  * `steps`: The total number of simulation steps for the `Dynamics` task.
  * `dt`: The time interval of each step, so the total simulation time is `steps * dt` for the `Dynamics` task.
  * `max_steps::Int`: Maximum number of steps to run the simulation for the `Relax` task. Default is `10000`.
  * `saver_item`: A `SaverItem` instance or a list of `SaverItem` instances. These are custom data-saving utilities that can be used to store additional quantities during the simulation (e.g., guiding centers or other derived values). If `nothing`, no additional data is saved beyond the default.
  * `call_back`: A user-defined function or `nothing`. If provided, this function will be called at every step, allowing for real-time inspection or manipulation of the simulation state.
  * `stopping_dmdt::Float64`: Primary stopping condition for both `LLG` and `SD` drivers. For standard micromagnetic simulations, typical values range from `0.01` to `1`. In `SD` driver mode, where time is not strictly defined, a factor of `γ` is applied to make it comparable to the `LLG` driver. For atomistic models using dimensionless units, set `using_time_factor` to `false` to disable this factor.
  * `relax_data_interval::Int`: Interval for saving overall data such as energies and average magnetization during a `Relax` task. A negative value disables data saving (e.g., `relax_data_interval = -1` saves data only at the end of the relaxation).
  * `dynamic_data_save::Bool`: Boolean flag to enable or disable saving overall data such as energies and average magnetization during the `Dynamics` task. Set to `true` to enable, or `false` to disable.
  * `relax_m_interval::Int`: Interval for saving magnetization data during a `Relax` task. A negative value disables magnetization saving.
  * `dynamic_m_interval::Int`: Interval for saving magnetization data during a `Dynamics` task. A negative value disables magnetization saving.
  * `using_time_factor::Bool`: Boolean flag to apply a time factor in `SD` mode for comparison with `LLG` mode. Default is `true`.
  * `save_vtk::Bool`: Boolean flag to save the magnetization to vtk files after finishing each task. Default is `false`.

#### Example

See examples at [High-Level Interface](@ref).

#### Notes

  * **Suffix Usage**: Parameters like `H`, `Ms`, `Ku`, `A`, `D`, `task`, and `driver` can be defined as arrays using the `_s` or `_sweep` suffix. When using these suffixes, ensure that the corresponding array lengths match. This allows the simulation to iterate over different values for these parameters.
  * **Argument Types**: The `args` parameter can be either a `NamedTuple` or a `Dict`, providing flexibility in how you organize and pass the simulation parameters.
  * **Driver Selection**: The `driver` parameter (or `driver_s` for multiple drivers) specifies the simulation type. Options include `"SD"` for the steepest-descent method, `"LLG"` for the Landau-Lifshitz-Gilbert equation, and `"LLG_STT"` for simulations involving spin-transfer torques.
  * **Stopping Criterion**: The `stopping_dmdt` parameter is critical for determining when to stop a simulation, particularly in relaxation tasks. It measures the rate of change in magnetization, with typical values ranging from `0.01` to `1`. For atomistic models, the `using_time_factor` flag can be set to `false` to disable time scaling.
  * **Data Saving**: The `relax_m_interval` and `dynamic_m_interval` parameters control how frequently magnetization data is saved during `Relax` and `Dynamics` tasks, respectively. Use negative values to disable data saving for these tasks.
