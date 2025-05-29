```
varest(x, method::NoiseEstimation; batch_size = 0, summary = mean)
```

Estimates the noise variance of a signal `x` using a given method

**Inputs**

  * `x`: Signal
  * `method`: Noise estimation method

      * `BayesianEst`: Bayesian noise estimation (To be implemented)
      * `GCVEst`: Generalized Cross-Validation (GCV) noise estimation
      * `LCurveEst`: L-curve noise estimation
      * `DerricoEst`: D'Errico noise estimation
  * `batch_size::Int`: Batch size for batch processing (default = 0)
  * `summary`: Summary function for batch processing (default = mean)
