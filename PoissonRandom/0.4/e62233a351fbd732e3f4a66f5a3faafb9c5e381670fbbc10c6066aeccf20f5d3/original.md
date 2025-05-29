```julia
pois_rand(λ)
pois_rand(rng::AbstractRNG, λ)
```

Generates Poisson(λ) distributed random numbers using a fast polyalgorithm.

## Examples

```julia
# Simple Poisson random
pois_rand(λ)

# Using another RNG
using RandomNumbers
rng = Xorshifts.Xoroshiro128Plus()
pois_rand(rng,λ)
```
