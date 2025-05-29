Package: ForecastPlots

```
pacf(x,
     type = "step-real",
     lag = Integer(ceil(10*log10(length(x)))),
     alpha = (0.95,0.99);
     plot = true)
```

Compute the partial auto-correlation for an univariate series with an optional plot.

There are two versions; the "step" version estimates the auto-regressive parameters of an increasing model, the "real" version estimates the actual partial auto-correlation by eliminating the linear information provided by the lags. When using the default type "stepwise-real" both versions are calculated.

The distribution used to estimate the confidence intervals is an approximation of a Fisher Transformation via a Normal Distribution. There is a plot recipe for the returned object.

# Arguments

  * `x`: Vector of data.
  * `type` = Valid values are "stepwise", "real" and "stepwise-real".
  * `lag`: Maximum number of lags.
  * `alpha`: A tuple with two thresholds (t1,t2) with t1 <= t2 to plot confidence intervals. The default values are 0.95 and 0.99.
  * `plot`: When true displays a plot with the results.

# Returns

A CF object

# Examples

```julia-repl
x = rand(100);
pacf(x);
pacf(x; plot=false)
20×2 Matrix{Float64}:
 -0.0475437   -0.101204
  0.0407006    0.058935
 -0.0747269    0.0366026
```
