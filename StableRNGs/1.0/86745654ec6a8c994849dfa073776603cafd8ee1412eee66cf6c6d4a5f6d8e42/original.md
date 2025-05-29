```
LehmerRNG
StableRNG
```

Simple RNG with stable streams, usually suitable for testing. Use only the alias `StableRNG`, as the name `LehmerRNG` is not part of the API.

Construction: `StableRNG(seed::Integer)`.

Seeding: `Random.seed!(rng::StableRNG, seed::Integer)`.
