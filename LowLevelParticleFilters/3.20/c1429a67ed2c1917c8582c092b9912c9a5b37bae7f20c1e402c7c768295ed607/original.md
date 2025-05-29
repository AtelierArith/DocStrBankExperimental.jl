```
unscentedplot(ukf;          n_std = 2, N = 100, dims=1:2)
unscentedplot(sigmapoints;  n_std = 2, N = 100, dims=1:2)
```

Plot the sigma points and their corresponding covariance ellipse. `dims` indicate the two dimensions to plot, and defaults to the first two dimensions.

If an UKF is passed, the sigma points after the last dynamics update are extracted from the filter. To plot the sigma points of the output, pass those in manually, they are available as `ukf.measurement_model.cache.x0` and `ukf.measurement_model.cache.x1`, denoting the input and output points of the measurement model.

Note: The covariance of the sigma points does not in general equal the predicted covariance of the state, since the state covariance is updated as `cov(sigmapoints) + R1`. Only when `AUGD = true` (augmented dynamics), the covariance of the state is given by the first `nx` sigmapoints.

See also `covplot`.

!!! note
    This function requires `using Plots` to be called before it is used.

