```
ess_is(weights; reff=1)
```

Estimate effective sample size (ESS) for importance sampling over the sample dimensions.

Given normalized weights $w_{1:n}$, the ESS is estimated using the L2-norm of the weights:

$$
\mathrm{ESS}(w_{1:n}) = \frac{r_{\mathrm{eff}}}{\sum_{i=1}^n w_i^2}
$$

where $r_{\mathrm{eff}}$ is the relative efficiency of the `log_weights`.

```
ess_is(result::PSISResult; bad_shape_nan=true)
```

Estimate ESS for Pareto-smoothed importance sampling.

!!! note
    ESS estimates for Pareto shape values $k > 0.7$, which are unreliable and misleadingly high, are set to `NaN`. To avoid this, set `bad_shape_nan=false`.

