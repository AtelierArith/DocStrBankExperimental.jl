```
sampleparticles(bm, nparticles, burnin)
```

Samples in the Boltzmann Machine model `bm` by running `nparticles` parallel, randomly initialized Gibbs chains for `burnin` steps. Returns particles containing `nparticles` generated samples. See also: `Particles`.
