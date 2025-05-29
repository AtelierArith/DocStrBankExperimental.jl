```
shuffle([rng=GLOBAL_RNG,] addr::Address, args...)
```

Traced execution of `shuffle`, where `addr` specifies the name / address of the random choice. By default, the address `addr` is ignored, but it can be intercepted to support inference in a probabilistic programming system. An `Address` is either a `Symbol`, or a `Pair` that begins with a `Symbol`.
