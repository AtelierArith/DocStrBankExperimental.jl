```
struct HaltonSampling <: SamplingStyle end
```

Sampling according to a Halton sequence

!!! note



Halton is a sequence, not a distribution, hence this sampling strategy repeats   realizations since the draws are not randomized; to draw different parameters,   one needs to provide a starting point in the sequence (start = 1 by default)
