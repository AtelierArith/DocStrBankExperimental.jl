```
LatinHypercubeSample(rng::AbstractRNG = Random.GLOBAL_RNG) <: RandomSamplingAlgorithm
```

A Latin Hypercube is a point set with the property that every one-dimensional interval `(i/n, i+1/n)` contains exactly one point. This is a good way to sample a high-dimensional space, as it is more uniform than a random sample but does not require as many points as a full net.
