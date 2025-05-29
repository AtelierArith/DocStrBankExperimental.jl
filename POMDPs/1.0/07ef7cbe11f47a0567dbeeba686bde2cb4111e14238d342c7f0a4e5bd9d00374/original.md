```
rand(rng::AbstractRNG, d::Any)
```

Return a random element from distribution or space `d`.

If `d` is a state or transition distribution, the sample will be a state; if `d` is an action distribution, the sample will be an action or if `d` is an observation distribution, the sample will be an observation.
