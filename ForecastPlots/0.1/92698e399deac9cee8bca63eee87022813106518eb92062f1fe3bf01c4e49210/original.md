Package: ForecastPlots

```
ccf(x1::{AbstractVector,DataFrame},
    x2::{AbstractVector,DataFrame};
    type = "cor",
    lag = Integer(ceil(10*log10(length(x1)))),
    alpha = (0.95,0.99);
    plot = true)
```

Compute the cross-correlation or cros-covariance of two univariate series with an optional plot

The results are normalized to preserve homoscedasticity. The distribution used to normalize the data is an approximation of a Fisher Transformation via a Normal Distribution. There is a plot recipe for the returned object, if the type is `cor` the plot will also show confidence intervals for the given alpha values.

If, for a given integer `k`, `x2` repeats `x1` values such that x1[t] = x2[t+k] for all `i` then high correlation value will be placed *at the right from the center* in the results. That is, this convention will be represented in the plots as `x1_t = x2_{t+k} -> _____0__k__` meaning x2 behavior can be predicted by x1 in k units.

# Arguments

  * `x1`: Vector or uni-dimensional DataFrame of data.
  * `x2`: Vector or uni-dimensional DataFrame of data.
  * `type`: Valid values are "cor" for correlation (default) and "cov" for convariance.
  * `lag`: Maximum number of lags.
  * `alpha`: A tuple with two thresholds (t1,t2) with t1 <= t2 to plot confidence intervals. The default values are 0.95 and 0.99.
  * `plot`: When true displays a plot with the results.

# Returns

Cros-correlation vector with an optional plot

# Examples

```julia-repl
x1 = rand(100);
x2 = circshift(x1,6);
ccf(x1, x2; type="cor");
ccf(x1, x2; type="cor", plot = false)
41-element Vector{Float64}:
  0.09861519494432992
 -0.04384418688776631
 -0.1900182513825246
  [...]
```
