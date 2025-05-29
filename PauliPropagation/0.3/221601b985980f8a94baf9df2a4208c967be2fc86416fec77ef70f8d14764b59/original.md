```
applytoall!(gate::AmplitudeDampingNoise, theta, psum, aux_psum; kwargs...)
```

Overload of `applytoall!` for `AmplitudeDampingNoise` gates.  It fixes the type-instability of the apply() function and reduces moving Pauli strings between psum and aux*psum. `psum` and `aux*psum` are merged later.
