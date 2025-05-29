```
ScoreGradELBO(n_samples; kwargs...)
```

Evidence lower-bound objective computed with score function gradient with the VarGrad objective, also known as the leave-one-out control variate.

# Arguments

  * `n_samples::Int`: Number of Monte Carlo samples used to estimate the VarGrad objective.

# Requirements

  * The variational approximation $q_{\lambda}$ implements `rand` and `logpdf`.
  * `logpdf(q, x)` must be differentiable with respect to `q` by the selected AD backend.
  * The target distribution and the variational approximation have the same support.
