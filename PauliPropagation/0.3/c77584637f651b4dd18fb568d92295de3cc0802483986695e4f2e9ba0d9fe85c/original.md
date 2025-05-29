```
applytoall!(gate::PauliNoise, p, psum, aux_psum; kwargs...)
```

Overload of `applytoall!` for `PauliNoise` gates with noise strength `p`.  It changes the coefficients in-place and does not require the `aux_psum`, which stays empty.
