```
rand!(v::AbstractVector, lmm::LMM) = rand!(default_rng(), v, lmm, lmm.result.theta, lmm.result.beta)
```

Generate random responce vector for fitted 'lmm' model, store results in `v`.
