```
rand_tangent([rng::AbstractRNG,] x)
```

Returns a arbitary tangent vector *appropriate* for the primal value `x`. Note that despite the name, no promises on the statistical randomness are made. Rather it is an arbitary value, that is generated using the `rng`.
