```
autofit_dist(SampleData; DistFit=nothing, FitLib=nothing, sort="AIC", verbose=false)
```

Fits a list of candidate distributions to the provided sample data, computes goodness-of-fit statistics, and returns a DataFrame summarizing the results.

# Arguments

  * `SampleData`: Array of sample data.
  * `DistFit` (optional): Array of distribution types to attempt (e.g., `[Normal, Gamma, Exponential]`). Each element must be a type that is a subtype of `Distribution`. If provided, this overrides `FitLib`.
  * `FitLib` (optional): Symbol indicating a predefined library of distributions to use. Valid options include `:all`, `:continuous`, or `:discrete`. Defaults to `:continuous` if neither `DistFit` nor `FitLib` is provided.
  * `sort` (optional): String indicating the criterion to sort the results. Options include `"ad"`, `"ks"`, `"ll"`, or `"AIC"`. Defaults to `"AIC"`.
  * `verbose` (optional): Boolean flag indicating whether to print warnings for distributions that fail to fit. Defaults to `false`.

# Returns

A DataFrame with the following columns:

  * `DistName`: The name of the distribution type.
  * `ADTest`: Anderson-Darling test statistic.
  * `KSTest`: Kolmogorov-Smirnov test statistic.
  * `AIC`: Akaike Information Criterion.
  * `AICc`: Corrected AIC.
  * `LogLikelihood`: Log-likelihood of the fit.
  * `FitParams`: The parameters of the fitted distribution.
