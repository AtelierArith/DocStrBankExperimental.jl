```
ProximalLocationScaleEntropy()
```

Proximal operator for the entropy of a location-scale distribution, which is defined as

$$
    \mathrm{prox}(\lambda) = \argmin_{\lambda^{\prime}} - \mathbb{H}(q_{\lambda^{\prime}}) + \frac{1}{2 \gamma_t} \left\lVert \lambda - \lambda^{\prime} \right\rVert ,
$$

where $\gamma_t$ is the stepsize the optimizer used with the proximal operator. This assumes the variational family is `<:VILocationScale` and the optimizer is one of the following:

  * `DoG`
  * `DoWG`
  * `Descent`

For ELBO maximization, since this proximal operator handles the entropy, the gradient estimator for the ELBO must ignore the entropy term. That is, the `entropy` keyword argument of `RepGradELBO` muse be one of the following:

  * `ClosedFormEntropyZeroGradient`
  * `StickingTheLandingEntropyZeroGradient`
