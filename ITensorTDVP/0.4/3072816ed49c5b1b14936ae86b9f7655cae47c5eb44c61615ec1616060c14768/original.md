```
tdvp(operator, t::Number, init::MPS; time_step, nsteps, kwargs...)
```

Use the time dependent variational principle (TDVP) algorithm to compute `exp(t * operator) * init` using an efficient algorithm based on alternating optimization of the MPS tensors and local Krylov exponentiation of `operator`.

Specify one of `time_step` or `nsteps`. If they are both specified, they must satisfy `time_step * nsteps == t`. If neither are specified, the default is `nsteps=1`, which means that `time_step == t`.

Returns:

  * `state::MPS` - time-evolved MPS
