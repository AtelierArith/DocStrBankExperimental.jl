```julia
stp(
    t_end,
    param,
    all_events_times,
    is_pre_or_post_index;
    _plot,
    nu_stp,
    kwargs...
)

```

This function performs the simulation of the presynaptic side.

# Arguments:

  * `t_end` end of simulation time
  * `param` named tuple with parameters, example: `(τ_rec = 20000, δ_decay	= .0004, tau_pre = 20, tau_soma = 40)`
  * `all_events_times` sorted list of times of external events
  * `is_pre_or_post_index` whether the external events are pre (`true`) or post (`false`)

# Keyword arguments

  * `_plot = false` whether to plot the result or not
  * `nu_stp = stp_build_transition_matrix()` transition matrix

# Output

  * `is_glu_release` `true` (success) or `false` (failure), list of presynaptic stimuli in `all_events_index` that led to a vesicle (glutamate) release
  * `D`, also (XD[2,:]), the evolution of the docked pool
  * `R`, also (XD[3,:]), the evolution of the reserve pool
  * `time` simulation times
  * `glu_release_times` the vector of times in which a successful releases (glutamate) occurred
  * `bap_by_epsp_times` the vector of times in which an AP was triggered by an EPSP
