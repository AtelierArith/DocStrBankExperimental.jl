```
estimated_time_to_merger(M, ν, v)
estimated_time_to_merger(pnsystem)
```

Compute the lowest-order PN approximation for the time to merger, starting from PN velocity parameter `v`.

This is used internally as a convenient way to estimate how long the inspiral integration should run for; we don't want it to integrate forever if PN has broken down.  However, it can be a very poor approximation, especially close to merger, and doubly so if the spins or eccentricity are significant.
