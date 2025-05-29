```julia
struct SawTooth
```

Callable (functor) struct defining sawtooth function for cyclic voltammetry.

`(::SawTooth)(t)` returns the voltage to be applied at moment t.

  * `vmin::Float64`: Minimum voltage. Default: -1V.
  * `vmax::Float64`: Maximum voltage. Default: 1V.
  * `scanrate::Float64`: Scan rate. Default: 0.1V/s.
  * `vstart::Float64`: Start voltage. Default: 0V
  * `tstart::Float64`: Start time. Default: 0s
  * `scanup::Bool`: Initial scan direction. Default: true
