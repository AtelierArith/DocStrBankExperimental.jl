```
OptimalWeights <: ComputedWeights
```

Optimal weighting, i.e., `w[l] = 1/v[l] * 1/(1+v[l]/λ)`.

# Constructors

  * `OptimalWeights(v=noisevar, λ=signalvar)` for known noise variances `noisevar` and signal variance `signalvar`
  * `OptimalWeights(λ=signalvar)` for known signal variance `signalvar`; noise variances will be estimated from data
  * `OptimalWeights(v=noisevar)` for known noise variances `noisevar`; signal variance will be estimated from data
  * `OptimalWeights()` for unknown noise and signal variances; noise and signal variances will be estimated from data
