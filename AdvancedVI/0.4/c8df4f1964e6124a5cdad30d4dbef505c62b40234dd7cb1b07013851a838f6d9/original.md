```
RepGradELBO(n_samples; kwargs...)
```

Evidence lower-bound objective with the reparameterization gradient formulation[^TL2014][^RMW2014][^KW2014]. This computes the evidence lower-bound (ELBO) through the formulation:

$$
\begin{aligned}
\mathrm{ELBO}\left(\lambda\right)
&\triangleq
\mathbb{E}_{z \sim q_{\lambda}}\left[
  \log \pi\left(z\right)
\right]
+ \mathbb{H}\left(q_{\lambda}\right),
\end{aligned}
$$

# Arguments

  * `n_samples::Int`: Number of Monte Carlo samples used to estimate the ELBO.

# Keyword Arguments

  * `entropy`: The estimator for the entropy term. (Type `<: AbstractEntropyEstimator`; Default: `ClosedFormEntropy()`)

# Requirements

  * The variational approximation $q_{\lambda}$ implements `rand`.
  * The target distribution and the variational approximation have the same support.
  * The target `logdensity(prob, x)` must be differentiable with respect to `x` by the selected AD backend.

Depending on the options, additional requirements on $q_{\lambda}$ may apply.
