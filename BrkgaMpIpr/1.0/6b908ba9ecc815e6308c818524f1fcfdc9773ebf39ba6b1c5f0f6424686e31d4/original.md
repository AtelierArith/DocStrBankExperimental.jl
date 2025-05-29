```
mutable struct ExternalControlParams
```

Represents additional control parameters that can be used outside this framework. You can load these parameters from a configuration file using [`load_configuration`](@ref) and [`build_brkga`](@ref), and write them using [`write_configuration`](@ref).

## Fields

  * `exchange_interval`: Interval at which elite chromosomes are exchanged (0 means no exchange) [> 0].

  * `num_exchange_indivuduals`: Number of elite chromosomes exchanged from each population [> 0].

  * `reset_interval`: Interval at which the populations are reset (0 means no reset) [> 0].
