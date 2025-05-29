```
mo_sys_from_particles(P::AbstractStateSpace; sparse = nparticles(P.A) > 500)
```

Converts a state-space model with `Particles` coefficients to a single state-space model with the same number of inputs as `P`, but with `nparticles(P.A)` times the output and state dimensions.

If `sparse` is true, the resulting model will be a `HeteroStateSpace` with sparse `A`, `C`, and `D` matrices.
