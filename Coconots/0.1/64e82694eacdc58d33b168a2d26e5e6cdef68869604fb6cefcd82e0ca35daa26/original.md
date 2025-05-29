```
compute_scores(cocoReg_fit, max_x = 50)
```

Computes scoring metrics for a fitted count regression model. The scores include the logarithmic score, quadratic score, and ranked probability score.

# Arguments

  * `cocoReg_fit`: A dictionary containing the fitted model results with keys such as `"data"`, `"parameter"`, `"order"`, `"type"`, and optionally `"covariates"` and `"max_loop"`.
  * `max_x` (optional): The maximum count value to use when summing the probability mass function (default is 50).

# Returns

A dictionary with the following keys:

  * `"logarithmic_score"`: The average negative log-probability of the observed counts.
  * `"quadratic_score"`: The average quadratic score based on computed probabilities and the h-index.
  * `"ranked_probability_score"`: The average ranked probability score.
