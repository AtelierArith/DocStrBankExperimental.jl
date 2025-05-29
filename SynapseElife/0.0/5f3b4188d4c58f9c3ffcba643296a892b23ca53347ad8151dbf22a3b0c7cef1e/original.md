```julia
evolveSynapse(
    xc0,
    xd0,
    p_synapse,
    events_sorted_times,
    is_pre_or_post_event,
    bap_by_epsp,
    is_glu_released,
    algos;
    verbose,
    progress,
    abstol,
    reltol,
    save_positions,
    nu,
    kwargs...
)

```

Perform a simulation of the synapse model. Among other things, you need to provide the external events impacting the synapse: Glutamate releases and BaPs.

# Arguments

  * `xc0` initial condition for the continuous variables. Example `xc0 = Synapse.initial_conditions_continuous_temp(p_synapse)`
  * `xd0` initial condition for the discrete variables. Example `xd0 = Synapse.initial_conditions_discrete(p_synapse)`
  * `p_synapse::SynapseParams` synapse parameters. Example `p_synapse = SynapseParams()`.
  * `events_sorted_times` sorted list of times (ms) for external events (Glutamate / BaP)
  * `is_pre_or_post_event::Vector{Bool}` whether the corresponding event in `events_sorted_times` is a Glutamate event. If `false`, it corresponds to a BaP event.
  * `bap_by_epsp::Vector{<:Real}` Additionnal BaPs time events, these are evoked by EPSPs. There are added to the ones indexed in `is_events_glu`.
  * `is_glu_released::Vector{Bool}` variable to shut down the Glutamate event, i.e. make the glutamate amplitude be zero. This proves useful to have this variable for reproducing some experiments. If equals to `false`, then glutamate amplitude is set to zero.
  * `algos` simulation algorithms from `PiecewiseDeterministicMarkovProcesses`. For example `(PDMP.CHV(:lsoda), PDMP.CHV(:lsoda))`

# Optional arguments

  * `verbose = false` display information during simulation
  * `abstol = 1e-8` absolute tolerance for ODE time stepper
  * `reltol = 1e-7` relative tolerance for ODE time stepper
  * `progress = false` show a progressbar during simulation
  * `save_positions = (false, true)` save the values (before, after) the jumps (transitions)
  * `nu` transition matrix. It is initialised with `buildTransitionMatrix()`.
