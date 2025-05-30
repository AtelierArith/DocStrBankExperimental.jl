```
forestplot(chains::Chains[, params::Vector{Symbol}]; kwargs...)
```

Generate a forest or caterpillar plot for the samples of the parameters `params` in `chains`.

By default, all parameters are plotted.

## Keyword arguments

  * `ordered` (default: `false`): If `ordered = false`, a forest plot is generated. If `ordered = true`, a caterpillar plot is generated.
  * `fill_q` (default: `false`) and `fill_hpd` (default: `true`): Fill the area below the curve in the quantiles interval (`fill_q = true`) or the highest posterior density (HPD) interval (`fill_hpd = true`). If both `fill_q = false` and `fill_hpd = false`, then the whole area below the curve is filled. If no fill color is desired, it should be specified with series attributes. These options are mutually exclusive.
  * `show_mean` (default: `true`) and `show_median` (default: `true`): Plot a vertical line of the mean (`show_mean = true`) or median (`show_median = true`) of the posterior density estimate. If both options are set to `true`, both lines are plotted.
  * `show_qi` (default: `false`) and `show_hpdi` (default: `true`): Plot a quantile interval (`show_qi = true`) or the largest HPD interval (`show_hpdi = true`) at the bottom of each density plot. These options are mutually exclusive.
  * `q` (default: `[0.1, 0.9]`): The two quantiles used for plotting if `fill_q = true` or `show_qi = true`.
  * `hpd_val` (default: `[0.05, 0.2]`): The complementary probability mass(es) of the highest posterior density intervals that are plotted if `fill_hpd = true` or `show_hpdi = true`.
