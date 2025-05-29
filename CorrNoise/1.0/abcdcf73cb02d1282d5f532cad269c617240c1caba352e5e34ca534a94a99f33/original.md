```
GaussRNG(flatrng::AbstractRNG)
GaussRNG(seed=0)
```

Initialize a Gaussian RNG. The parameter `flatrng` must be a uniform RNG. If a `seed` is used, then a `MersenneTwister` RNG is used.
