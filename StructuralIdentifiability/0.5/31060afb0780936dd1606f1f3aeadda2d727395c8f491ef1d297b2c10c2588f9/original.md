```
assess_local_identifiability(ode::ODE{P}; funcs_to_check::Array{<: Any, 1}, prob_threshold::Float64=0.99, type=:SE, loglevel=Logging.Info) where P <: MPolyRingElem{Nemo.QQFieldElem}
```

Checks the local identifiability/observability of the functions in `funcs_to_check`. The result is correct with probability at least `prob_threshold`.

Call this function if you have a specific collection of parameters of which you would like to check local identifiability.

`type` can be either `:SE` (single-experiment identifiability) or `:ME` (multi-experiment identifiability). If the type is `:ME`, states are not allowed to appear in the `funcs_to_check`.
