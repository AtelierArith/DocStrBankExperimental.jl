```
denoising(y::AbstractArray, alg)
```

Denoises a signal `y`

**Inputs**

  * `y`: Noisy signal
  * `alg`: Denoising method

      * `BayesDenoising`: Bayesian Regularization denoising method (to be implemented)
      * `GCVDenoising`: GCV denoising method
      * `LCurveDenoising`: L-curve denoising method
      * `KalmanDenoising`: Kalman filter denoising method

**Output**

  * `x`: Denoised signal
