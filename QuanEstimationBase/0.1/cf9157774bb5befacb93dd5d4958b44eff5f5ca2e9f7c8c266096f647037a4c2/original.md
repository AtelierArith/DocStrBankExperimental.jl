```
MeasurementOpt(mtype=:Projection, kwargs...)
```

Measurement optimization.

  * `mtype`: The type of scenarios for the measurement optimization. Options are `:Projection` (default), `:LC` and `:Rotation`.
  * `kwargs...`: keywords and the correponding default vaules. `mtype=:Projection`, `mtype=:LC` and `mtype=:Rotation`, the `kwargs...` are `M=nothing`, `B=nothing, POVM_basis=nothing`, and `s=nothing, POVM_basis=nothing`, respectively.
