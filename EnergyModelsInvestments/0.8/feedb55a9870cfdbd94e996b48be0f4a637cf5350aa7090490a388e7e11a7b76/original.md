```
SemiContinuousInvestment <: Investment
```

Semi-continuous investments, that is the added capacity is either zero or between a minimum and a maximum value. In this subtype, the cost is crossing the origin, that is the CAPEX is still linear dependent on the

Semi-continuous investments introduce one binary variable for each investment period.

# Fields

  * **`min_add::TimeProfile`** is the minimum added capacity in an investment period. In the case of `SemiContinuousInvestment`, this implies that the model **must** invest at least in this capacity in each investment period. in this capacity in each investment period where the model decides to invest. The model can also choose not too invest at all.
  * **`max_add::TimeProfile`** is the maximum added capacity in an investment period.
