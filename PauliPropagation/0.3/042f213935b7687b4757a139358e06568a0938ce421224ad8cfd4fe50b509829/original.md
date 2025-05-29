```
applytoall!(gate::TGate, thetas, psum, aux_psum; kwargs...)
```

Overload of `applytoall!()` for `TGate(qind)`. Redirects to a `PauliRotation(:Z, qind)` with angle π/4.
