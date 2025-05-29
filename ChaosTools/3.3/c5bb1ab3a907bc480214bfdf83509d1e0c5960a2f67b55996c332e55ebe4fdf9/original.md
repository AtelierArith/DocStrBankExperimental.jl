```
first_return_times(ds::DynamicalSystem, u0, εs, T; diffeq = NamedTuple(), kwargs...) → t
```

Return the first return times `t` to the sets centered at `u0` with radii `εs` for the given dynamical system. Time evolution of `ds` always starts from `u0`.

This function operates on the same principles as [`exit_entry_times`](@ref), so see that docstring for more info on `u0, εs`. The only differences here are:

1. If the system did not return to the set within time `T`, then `0` is returned.
2. For continuous systems, the exact returned time is from start of time evolution, up to the time to get closest back to `u0`, provided that this is at least `ε`-close.
