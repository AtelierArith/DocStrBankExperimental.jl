```
correlation_length(state, env::CTMRGEnv; num_vals=2, kwargs...)
```

Compute the correlation length associated to `state` as contracted using the environment `env`, based on the spectrum of the horizontal and vertical transfer matrices associated to `env`. Additionally the (normalized) eigenvalue spectrum is returned. The number of computed eigenvalues can be specified using `num_vals`, and any remaining keyword arguments are passed through to `MPSKit.transfer_spectrum` (e.g. allowing to target the correlation length in a specific symmetry sector).
