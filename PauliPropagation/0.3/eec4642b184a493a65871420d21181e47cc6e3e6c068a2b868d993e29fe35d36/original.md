```
applytoall!(gate::PauliRotation, theta, psum, aux_psum; kwargs...)
```

Overload of `applytoall!` for `PauliRotation` gates.  It fixes the type-instability of the `apply()` function and reduces moving Pauli strings between `psum` and `aux_psum`. `psum` and `aux_psum` are merged later.
