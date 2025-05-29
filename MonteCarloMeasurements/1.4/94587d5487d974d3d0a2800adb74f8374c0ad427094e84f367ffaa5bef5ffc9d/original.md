```
struct StaticParticles{T, N} <: AbstractParticles{T, N}
```

See `?Particles` for help. The difference between `StaticParticles` and `Particles` is that the `StaticParticles` store particles in a static vecetor. This makes runtimes much shorter, but compile times longer. See the documentation for some benchmarks. Only recommended for sample sizes of ≲ 300-400
