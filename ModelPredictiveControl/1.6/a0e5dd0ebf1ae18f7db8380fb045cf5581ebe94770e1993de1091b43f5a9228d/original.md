```
KalmanFilter(model, i_ym, nint_u, nint_ym, P̂_0, Q̂, R̂; direct=true)
```

Construct the estimator from the augmented covariance matrices `P̂_0`, `Q̂` and `R̂`.

This syntax allows nonzero off-diagonal elements in $\mathbf{P̂}_{-1}(0), \mathbf{Q̂, R̂}$.
