```
phaserec(array; radius = 0.6, maxsteps = 300, ϵ = 10^-5[, noise])
```

Reconstruct `array` which must be an array of booleans. This is equivalent to running `phaserec(two_point(array), size(array); ...)`.
