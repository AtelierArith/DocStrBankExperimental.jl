`pomp` is the constructor for the *PompObject* class.

```
pomp(
    data;
    t0, times, timevar,
    params,
    accumvars,
    rinit, rprocess,
    rmeasure, logdmeasure
    )
```

## Arguments

  * `data`: observations. The default constructor takes a vector of NamedTuples as data. One can also supply a DataFrame.
  * `t0`: zero time, t₀.
  * `times`: observation times. If `data` is supplied as a DataFrame, `times` should be a Symbol which is the time variable in the DataFrame.
  * `timevar`: optional symbol.  Name of the time variable.
  * `params`: parameters. A NamedTuple or vector of NamedTuples.
  * `accumvars`: a NamedTuple of state variables to be reset (usually to zero) immediately before each simulation stage.
  * `rinit`: simulator of the latent-state distribution at t₀. This component should be a function that takes parameters and, optionally, `t0`, the initial time.
  * `rprocess`: simulator of the latent-state process. This component should be a plugin (see [`euler`](@ref), [`onestep`](@ref), and [`discrete_time`](@ref)).
  * `rmeasure`: simulator of the measurement process. This component should be a function that takes states, parameters, and, optionally, `t`, the current time.
  * `logdmeasure`: log pdf of the measurement process. This component should be a function that takes data, states, parameters, and, optionally, `t`, the current time.
