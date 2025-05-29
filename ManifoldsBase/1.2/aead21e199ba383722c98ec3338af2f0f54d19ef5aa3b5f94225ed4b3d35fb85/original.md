```
Random.rand(M::AbstractManifold, [d::Integer]; vector_at=nothing)
Random.rand(rng::AbstractRNG, M::AbstractManifold, [d::Integer]; vector_at=nothing)
```

Generate a random point on manifold `M` (when `vector_at` is `nothing`) or a tangent vector at point `vector_at` (when it is not `nothing`).

Optionally a random number generator `rng` to be used can be specified. An optional integer `d` indicates that a vector of `d` points or tangent vectors is to be generated.

!!! note
    Usually a uniform distribution should be expected for compact manifolds and a Gaussian-like distribution for non-compact manifolds and tangent vectors, although it is not guaranteed. The distribution may change between releases.

    `rand` methods for specific manifolds may take additional keyword arguments.

