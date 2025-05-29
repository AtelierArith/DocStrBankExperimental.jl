```
ProbabilityWeights(vs, wsum=sum(vs))
```

Construct a `ProbabilityWeights` vector with weight values `vs`. A precomputed sum may be provided as `wsum`.

Probability weights represent the inverse of the sampling probability for each observation, providing a correction mechanism for under- or over-sampling certain population groups. These weights may also be referred to as sampling weights.
