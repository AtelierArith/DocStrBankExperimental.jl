```
applytoall!(gate::FrozenGate, thetas, psum, aux_psum; kwargs...)
```

Overload of `applytoall!` for `FrozenGate`s. Re-directs to `applytoall!` for the wrapped `FrozenGate.gate` with the frozen parameter.
