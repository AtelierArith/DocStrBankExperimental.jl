```
sys_from_particles(P, i)
sys_from_particles(P)
```

Return the `i`th system from a system `P` with `Particles` coefficients.

If called without an index, return a vector of systems, one for each possible `i`.

This function is used to convert from an uncertain representation using `Particles` to a "multi-model" representation using multiple `StateSpace` models.

See also [`ss2particles`](@ref), [`mo_sys_from_particles`](@ref) and `MonteCarloMeasurements.nominal`.
