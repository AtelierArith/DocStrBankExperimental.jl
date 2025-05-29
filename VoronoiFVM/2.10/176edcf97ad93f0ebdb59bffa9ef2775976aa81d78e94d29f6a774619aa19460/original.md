```julia
prepare_diffeq!(state, jacval, tjac)

```

Prepare system for use with VoronoiFVMDiffEq.

  * `jacval`: value at which to evaluate jacobian to obtatin prototype
  * `tjac`: time moment for jacobian

Returns a prototype for the jacobian.
