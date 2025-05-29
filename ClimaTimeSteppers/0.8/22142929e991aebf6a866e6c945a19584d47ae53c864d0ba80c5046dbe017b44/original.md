```
Multirate(fast, slow)
```

A multirate Runge–Kutta scheme, combining `fast` and `slow` algorithms

`slow` can be any algorithm providing methods for the following functions

  * `init_inner(prob, outercache, dt)`
  * `update_inner!(innerinteg, outercache, f_slow, u, p, t, dt, stage)`

Algorithms which currently support this are:

  * [`LowStorageRungeKutta2N`](@ref)
  * [`MultirateInfinitesimalStep`](@ref)
  * [`WickerSkamarockRungeKutta`](@ref)
