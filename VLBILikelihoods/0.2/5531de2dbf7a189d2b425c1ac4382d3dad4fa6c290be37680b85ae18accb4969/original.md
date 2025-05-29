```
ClosurePhaseLikelihood(μ, Σ)
```

Construct the Gaussian approximate closure phase likelihood distribution. The distribution used here is not the exact distribution for closure phases since this becomes quite complicated (especially for correlated covariances). For our approximation we take the Gaussian around the complex exponential of the phase, that is the unormalized likelihood is given by

$$
    \log\mathcal{L} = -\frac{1}{2}(e^{i\theta} - e^{i\mu})^T\Sigma^{-1}(e^{i\theta} - e^{i\mu})
$$

If Σ is diagonal then this reduces to a bunch of independent Von Mises distributions, and if Σ is dense, this becomes a complicated multi-variate extension of the Von Mises distribution[^1].

# Parameters

  * `μ`: The mean closure phase, which is usually computed from some VLBI model
  * `Σ`: The measurement covariance matrix, which is usually computed directly from the data.      Note that `Σ` can either be a matrix or a vector. If `Σ` is a vector then we interpret      `Σ` to represent the diagonal of the covariance matrix.

!!! warning
    Note that for the dense Σ, the likelihood is not normalized properly since the normalization is not analytically tractable. This is not a problem for sampling since the normalizing constant does not depend on `μ` so it does not *usually* impact parameter estimation. However, if you are including terms that modify the covariance `Σ` then this likelihood is wrong and could give biased results. If you want to fit noise terms in Σ please either use the diagonal approximation to the likelihood, or **better yet** fit complex visibilities directly.


[^1]: This distribution is defined on the n torus where n is the number of closure phases.
