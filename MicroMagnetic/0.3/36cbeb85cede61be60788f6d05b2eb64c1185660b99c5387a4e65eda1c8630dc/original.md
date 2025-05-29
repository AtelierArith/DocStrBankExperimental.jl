```
relax(sim::AbstractSim; max_steps=10000, stopping_dmdt=0.01, save_data_every=100, 
       save_m_every=-1, using_time_factor=true)
```

Relaxes the system using either the `LLG` or `SD` driver. This function is compatible with both [Micromagnetic model](@ref) and [Atomistic spin model](@ref).

**Arguments:**

  * `max_steps::Int`: Maximum number of steps to run the simulation. Default is `10000`.
  * `stopping_dmdt::Float64`: Primary stopping condition for both `LLG` and `SD` drivers. For standard micromagnetic simulations, typical values range from `0.01` to `1`. In `SD` driver mode, where time is not strictly defined, a factor of `γ` is applied to make it comparable to the `LLG` driver. For atomistic models using dimensionless units, set `using_time_factor` to `false` to disable this factor.
  * `save_data_every::Int`: Interval for saving overall data such as energies and average magnetization. A negative value disables data saving (e.g., `save_data_every=-1` saves data only at the end of the relaxation).
  * `save_m_every::Int`: Interval for saving magnetization data. A negative value disables magnetization saving.
  * `using_time_factor::Bool`: Boolean flag to apply a time factor in `SD` mode for comparison with `LLG` mode. Default is `true`.

**Examples:**

```julia
    relax(sim, max_steps=10000, stopping_dmdt=0.1)
```
