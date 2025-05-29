```
covellipse(μ, Σ; showaxes=false, n_std=1, n_ellipse_vertices=100)
```

Plot a confidence ellipse of the 2×2 covariance matrix `Σ`, centered at `μ`. The ellipse is the contour line of a Gaussian density function with mean `μ` and variance `Σ` at `n_std` standard deviations. If `showaxes` is true, the two axes of the ellipse are also plotted.
