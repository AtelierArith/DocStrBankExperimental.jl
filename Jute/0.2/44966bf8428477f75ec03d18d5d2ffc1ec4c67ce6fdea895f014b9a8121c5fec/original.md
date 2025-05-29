```
fixed_rng(seed)
```

A local fixture that returns an `AbstractRNG` object seeded with `hash(seed)` (even if the given seed is already an integer).
