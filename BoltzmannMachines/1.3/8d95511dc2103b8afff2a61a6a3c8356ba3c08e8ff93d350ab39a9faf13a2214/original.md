```
gibbssample!(particles, bm, nsteps)
```

Performs Gibbs sampling on the `particles` in the Boltzmann machine model `bm` for `nsteps` steps. (See also: `Particles`.) When sampling in multimodal deep Boltzmann machines, in-between layers are assumed to contain only Bernoulli-distributed nodes.
