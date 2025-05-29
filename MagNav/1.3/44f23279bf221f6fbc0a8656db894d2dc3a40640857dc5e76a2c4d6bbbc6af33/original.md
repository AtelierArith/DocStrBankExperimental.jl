```
ekf_online_nn_setup(x, y, m, y_norms; N_sigma::Int = 1000)
```

Setup for extended Kalman filter (EKF) with online learning of neural network weights.

**Arguments:**

  * `x`:       `N` x `Nf` data matrix (`Nf` is number of features)
  * `y`:       length-`N` target vector
  * `m`:       neural network model, does not work with skip connections
  * `y_norms`: tuple of `y` normalizations, i.e., `(y_bias,y_scale)`
  * `N_sigma`: (optional) number of neural network weights sets to use to create `nn_sigma`

**Returns:**

  * `P0_nn`:    initial neural network weights covariance matrix
  * `nn_sigma`: initial neural network weights estimate std dev
