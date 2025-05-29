```
ssrand(T::Type, ny::Int, nu::Int, nstates::Int; proper=false, stable=true, Ts=nothing)
```

Returns a random `StateSpace` model with `ny` outputs, `nu` inputs, and `nstates` states, whose matrix elements are normally distributed.

It is possible to specify if the system should be `proper` or `stable`.

Specify a sample time `Ts` to obtain a discrete-time system.
