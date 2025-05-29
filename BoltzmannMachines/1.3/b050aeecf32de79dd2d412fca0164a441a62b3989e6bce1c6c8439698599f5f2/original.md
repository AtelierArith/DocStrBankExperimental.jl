```
gibbssamplecond!(particles, bm, cond, nsteps)
```

Conditional Gibbs sampling on the `particles` in the `bm` for `nsteps` Gibbs sampling steps.

The variables that are marked in the indexing vector `cond` are fixed to the initial values in `particles` during sampling. This way, conditional sampling is performed on these variables.

See also: `Particles`, `initparticles`
