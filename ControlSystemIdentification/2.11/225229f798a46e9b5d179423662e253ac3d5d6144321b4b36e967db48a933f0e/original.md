```
N4SIDStateSpace <: AbstractPredictionStateSpace
```

The result of statespace model estimation using the `n4sid` method.

# Fields:

  * `sys`: estimated model in the form of a `StateSpace` object
  * `Q`: estimated covariance matrix of the states
  * `R`: estimated covariance matrix of the measurements
  * `S`: estimated cross covariance matrix between states and measurements
  * `K`: Kalman observer gain
  * `P`: solution to the Riccatti equation
  * `x`: estimated state trajectory (`n4sid`) or initial condition (`subspaceid`)
  * `s`: singular value decomposition
  * `fve`: Fraction of variance explained by singular values
