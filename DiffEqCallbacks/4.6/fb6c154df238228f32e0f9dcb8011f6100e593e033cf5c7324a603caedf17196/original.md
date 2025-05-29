```julia
PresetTimeCallback(tstops, user_affect!;
    initialize = DiffEqBase.INITIALIZE_DEFAULT,
    filter_tstops = true,
    kwargs...)
```

A callback that adds callback `affect!` calls at preset times. No playing around with `tstops` or anything is required: this callback adds the triggers for you to make it automatic.

## Arguments

  * `tstops`: the times for the `affect!` to trigger at.
  * `user_affect!`: an `affect!(integrator)` function to use at the time points.

## Keyword Arguments

  * `filter_tstops`: Whether to filter out tstops beyond the end of the integration timespan. Defaults to true. If false, then tstops can extend the interval of integration.
