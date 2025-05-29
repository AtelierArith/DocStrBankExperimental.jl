```
PEtabParameter(x; kwargs...)
```

Parameter estimation information for parameter `x`.

All parameters to be estimated in a `PEtabODEProblem` must be declared as a `PEtabParameter`, and `x` must be the name of a parameter that appears in the model, observable formula, or noise formula.

## Keyword Arguments

  * `lb::Float64 = 1e-3`: The lower parameter bound for parameter estimation. Must    be specified on the linear scale. For example, if `scale = :log10`, provide the    bound as `1e-3` rather than `log10(1e-3)`.
  * `ub::Float64 = 1e3`: The upper parameter bound for parameter estimation. Must as for    `lb` be provided on linear scale.
  * `scale::Symbol = :log10`: The scale on which to estimate the parameter. Allowed options   are `:log10` (default), `:log2` `:log`, and `:lin`. Estimating on the `log10`   scale typically improves performance and is recommended.
  * `prior = nothing`: An optional continuous univariate parameter prior distribution from   [Distributions.jl](https://github.com/JuliaStats/Distributions.jl). The prior    overrides any parameter bounds.
  * `prior_on_linear_scale = true`: Whether the prior is on the linear scale (default) or on   the transformed scale. For example, if `scale = :log10` and   `prior_on_linear_scale = false`, the prior acts on the transformed value; `log10(x)`.
  * `estimate = true`: Whether the parameter should be estimated (default) or treated as a   constant.
  * `value = nothing`: Value to use if `estimate = false`, and value retreived by the `get_x`   function. Defaults to the midpoint between `lb` and `ub`.

## Description

If a prior $\pi(x_i)$ is provided, the parameter estimation problem becomes a maximum a posteriori problem instead of a maximum likelihood problem. Practically, instead of minimizing the negative log-likelihood,$-\ell(x)$, the negative posterior is minimized:

$$
\min_{\mathbf{x}} -\ell(\mathbf{x}) - \sum_{i} \pi(x_i)
$$

For all parameters $i$ with a prior.
