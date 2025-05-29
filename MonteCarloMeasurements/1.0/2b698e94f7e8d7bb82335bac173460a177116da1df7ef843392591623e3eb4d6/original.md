```
wasserstein(p1::AbstractParticles,p2::AbstractParticles,p)
```

Returns the Wasserstein distance (Earth-movers distance) of order `p`, to the `p`th power, between `p1` and `p2`. I.e., for `p=2`, this returns W₂²
