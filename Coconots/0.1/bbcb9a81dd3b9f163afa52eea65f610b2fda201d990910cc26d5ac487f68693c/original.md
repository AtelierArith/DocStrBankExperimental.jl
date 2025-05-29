```
cocoPit(cocoReg_fit, n_bins=21)
```

Calculates the Probability Integral Transform (PIT) histogram for a fitted count regression model.

# Arguments

  * `cocoReg_fit`: A dictionary containing the fitted model results. Expected keys include `"data"`, `"parameter"`, `"order"`, `"type"`, and optionally `"covariates"` and `"max_loop"`.
  * `n_bins` (optional): An integer specifying the number of bins to use for the PIT histogram (default is 21).

# Returns

A dictionary with:

  * `"Pit_values"`: A vector of differences between consecutive PIT values, representing the estimated histogram probabilities.
  * `"bins"`: A vector of bin edge values (excluding the initial zero).
