```
ContinuousInvestment <: Investment
```

Continuous investment between a lower and upper bound.

# Fields

  * **`min_add::TimeProfile`** is the minimum added capacity in an investment period. In the case of `ContinuousInvestment`, this implies that the model **must** invest at least in this capacity in each investment period.
  * **`max_add::TimeProfile`** is the maximum added capacity in an investment period.
