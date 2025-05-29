```
bootstrap([rng::AbstractRNG,] p::Particles, n = nparticles(p))
```

Return Particles resampled with replacement. `n` specifies the number of samples to draw. Also works for arrays of Particles, in which case a single set of indices are drawn and used to extract samples from all elements in the array.
