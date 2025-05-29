```
find_nanb(d::InputOutputData, na, nb; logrms = false, method = :aic)
```

Plots the RMSE and AIC For model orders up to `na`, `nb`. Useful for model selection. `na` can be either an integer or a range. The same holds for `nb`.

  * `logrms`: determines whether or not to plot the base 10 logarithm of the RMS error.
  * `method`: determines whether to use the Akaike Information Criterion (`:aic`) or the Final Prediction Error (`:fpe`) to determine the model order.

If the color scale is hard to read due to a few tiles representing very large errors, avoid drawing those tiles by providing ranges for `na` and `nb` instead of integers, e.g., avoid showing model order smaller than 2 using `find_nanb(d, 3:na, 3:nb)`
