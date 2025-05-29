```
assess_local_identifiability(dds::DDS{P}; funcs_to_check::Array{<: Any, 1}, known_ic, prob_threshold::Float64=0.99, loglevel=Logging.Info) where P <: MPolyRingElem{Nemo.QQFieldElem}
```

Checks the local identifiability/observability of the functions in `funcs_to_check`. The result is correct with probability at least `prob_threshold`. A list of quantities can be provided as `known_ic` for which the initial conditions can be assumed to be known and generic.
