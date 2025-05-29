```
parallelize(f, bd::Billiard, t, particles; partype = :threads)
```

Parallelize function `f` across the available particles. The parallelization type can be `:threads` or `:pmap`, which use threads or a worker pool initialized with `addprocs` *before* `using DynamicalBilliards`.

`particles` can be:

  * A `Vector` of particles.
  * An integer `n` optionally followed by an angular velocity `ω`. This uses [`randominside`](@ref).

The functions usable here are:

  * [`meancollisiontime`](@ref)
  * [`escapetime`](@ref)
  * [`lyapunovspectrum`](@ref) (returns only the maximal exponents)
  * [`boundarymap`](@ref) (returns vector of vectors of 2-vectors *and* `arcintervals`)
