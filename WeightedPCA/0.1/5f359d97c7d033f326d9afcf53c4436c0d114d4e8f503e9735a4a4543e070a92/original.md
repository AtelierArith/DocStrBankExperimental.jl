```
InverseVarianceWeights <: ComputedWeights
```

Inverse noise variance weighting, i.e., `w[l] = 1/v[l]`.

# Constructors

  * `InverseVarianceWeights(v=noisevar)` for known noise variances `noisevar`
  * `InverseVarianceWeights()` for unknown noise variances; noise variances will be estimated from data
