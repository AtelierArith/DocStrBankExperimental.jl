```
devresid(model::BetaRegressionModel)
```

Compute the signed deviance residuals of the model,

$$
\mathrm{sgn}(y_i - \hat{y}_i) \sqrt{2 \lvert \ell(y_i, \hat{\phi}) - \ell(\hat{y}_i, \hat{\phi}) \rvert}
$$

where $\ell$ denotes the log likelihood, $y_i$ is the $i$th observed value of the response, $\hat{y}_i$ is the $i$th fitted value, and $\hat{\phi}$ is the estimated common precision parameter.

See also: [`deviance`](@ref)
