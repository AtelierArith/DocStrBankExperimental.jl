```
extract_coefs(model::UnfoldModel, predictor, basisname)
```

Return the coefficients of an Unfold model for a certain `predictor` and `basisname`.

For extracting the terms of a predictor variable `predictor` must be a symbol e.g. :continuous. For extracting the intercept `predictor` should be a String, i.e. "(Intercept)".

`basisname` must match one of the basis names which can be found in `coeftable(model)`.

Note: If a predictor variable has more than one term in the formula (e.g. a spline set, a categorical variable with several levels or an interaction), the coefficients for all terms are returned.

The dimensions of the returned coefficients are channel x times x coefficients.
