```
PEtabObservable(obs_formula, noise_formula; kwargs...)
```

Formulas defining the likelihood that links the model output to the measurement data.

`obs_formula` describes how the model output relates to the measurement data, while `noise_formula` describes the standard deviation (measurement error) and can be an equation or a numerical value. Both the observable and noise formulas can be a valid Julia equation. Variables used in these formulas must be either model species, model parameters, or parameters defined as `PEtabParameter`. The formulas can also include time-point-specific noise and observable parameters; for more information, see the documentation.

## Keyword Argument

  * `transformation`: The transformation applied to the observable and its corresponding   measurements. Valid options are `:lin` (normal measurement noise), `:log`, `log2` or   `:log10` (log-normal measurement noise). See below for more details.

## Description

For a measurement `y`, an observable `h = obs_formula`, and a standard deviation `σ = noise_formula`, the `PEtabObservable` defines the likelihood that links the model output to the measurement data: $\pi(y \mid h, \sigma)$. For `transformation = :lin`, the measurement noise is assumed to be normally distributed, and the likelihood is given by:

$$
\pi(y|h, \sigma) = \frac{1}{\sqrt{2\pi \sigma^2}}\mathrm{exp}\bigg( -\frac{(y - h)^2}{2\sigma^2} \bigg)
$$

As a special case, if $\sigma = 1$, this likelihood reduces to the least-squares objective function. For `transformation = :log`, the measurement noise is assumed to be log-normally distributed, and the likelihood is given by:

$$
\pi(y|h, \sigma) = \frac{1}{\sqrt{2\pi \sigma^2 y^2}}\mathrm{exp}\bigg( -\frac{\big(\mathrm{log}(y) - \mathrm{log}(h)\big)^2}{2\sigma^2} \bigg)
$$

For `transformation = :log10`, the measurement noise is assumed to be log10-normally distributed, and the likelihood is given by:

$$
\pi(y|h, \sigma) = \frac{1}{\sqrt{2\pi \sigma^2 y^2}\mathrm{log}(10) }\mathrm{exp}\bigg( -\frac{\big(\mathrm{log}_{10}(y) - \mathrm{log}_{10}(h)\big)^2}{2\sigma^2} \bigg)
$$

Lastly, for `transformation = :log2`, the measurement noise is assumed to be log2-normally distributed, and the likelihood is given by:

$$
\pi(y|h, \sigma) = \frac{1}{\sqrt{2\pi \sigma^2 y^2}\mathrm{log}(2) }\mathrm{exp}\bigg( -\frac{\big(\mathrm{log}_{2}(y) - \mathrm{log}_{2}(h)\big)^2}{2\sigma^2} \bigg)
$$

For numerical stabillity, PEtab.jl works with the log-likelihood in practice.
