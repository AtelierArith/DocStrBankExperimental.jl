```
System(crystal::Crystal, moments, mode; dims=(1, 1, 1), seed=nothing)
```

A spin system is constructed from the [`Crystal`](@ref) unit cell, a specification of the spin `moments` symmetry-distinct sites, and a calculation `mode`. Interactions can be added to the system using, e.g., [`set_exchange!`](@ref). The default supercell dimensions are 1×1×1 chemical cells, but this can be changed with `dims`.

Spin `moments` comprise a list of pairs, `[i1 => Moment(...), i2 => ...]`, where `i1, i2, ...` are a complete set of symmetry-distinct atoms. Each [`Moment`](@ref) contains spin and $g$-factor information.

The two primary options for `mode` are `:SUN` and `:dipole`. In the former, each spin-$s$ degree of freedom is described as an SU(*N*) coherent state, i.e. a quantum superposition of $N = 2s + 1$ levels. This formalism can be useful to capture multipolar spin fluctuations or local entanglement effects. 

Mode `:dipole` projects the SU(*N*) dynamics onto the restricted space of pure dipoles. In practice this means that Sunny will simulate Landau-Lifshitz dynamics, but single-ion anisotropy and biquadratic exchange interactions will be renormalized to improve accuracy. To disable this renormalization, use the mode `:dipole_uncorrected`, which corresponds to the formal $s → ∞$ limit. For details, see the documentation page: [Interaction Renormalization](@ref).

Stochastic operations on this system can be made reproducible by selecting a `seed` for this system's pseudo-random number generator. The default system seed will be generated from Julia's task-local RNG, which can itself be seeded using `Random.seed!`.

All spins are initially polarized in the global $z$-direction.
