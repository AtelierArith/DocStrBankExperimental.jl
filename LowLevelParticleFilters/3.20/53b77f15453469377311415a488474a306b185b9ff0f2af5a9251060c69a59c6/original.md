```
covplot(μ, Σ; n_std = 2, dims=1:2)
covplot(kf; n_std = 2, dims=1:2)
```

Plot the covariance ellipse of the state `μ` and covariance `Σ`. `dims` indicate the two dimensions to plot, and defaults to the first two dimensions.

If a Kalman-type filter is passed, the state and covariance are extracted from the filter.

See also `unscentedplot`.

!!! note
    This function requires `using Plots` to be called before it is used.

