```
UKFWeights
```

Weights for the Unscented Transform.

Sigmapoints are by convention ordered such that the center (mean) point is first.

# Fields

  * `wm`: center weight when computing mean
  * `wc`: center weight when computing covariance
  * `wmi`: off-center weight when computing mean
  * `wci`: off-center weight when computing covariance
  * `W`: Cholesky weight
