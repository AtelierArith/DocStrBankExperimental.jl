```
BossOptions(; kwargs...)
```

Stores miscellaneous settings of the BOSS algorithm.

# Keywords

  * `info::Bool`: Setting `info=false` silences the BOSS algorithm.
  * `debug::Bool`: Set `debug=true` to print stactraces of caught optimization errors.
  * `parallel_evals::Symbol`: Possible values: `:serial`, `:parallel`, `:distributed`. Defaults to `:parallel`.       Determines whether to run multiple objective function evaluations       within one batch in serial, parallel, or distributed fashion.       (Only has an effect if batching AM is used.)
  * `callback::BossCallback`: If provided, `callback(::BossProblem; kwargs...)`       will be called before the BO procedure starts and after every iteration.

See also: [`bo!`](@ref)
