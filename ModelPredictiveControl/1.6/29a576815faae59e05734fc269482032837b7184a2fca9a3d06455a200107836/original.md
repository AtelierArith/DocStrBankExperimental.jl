```
SteadyKalmanFilter(model, i_ym, nint_u, nint_ym, Q̂, R̂; direct=true)
```

Construct the estimator from the augmented covariance matrices `Q̂` and `R̂`.

This syntax allows nonzero off-diagonal elements in $\mathbf{Q̂, R̂}$.
