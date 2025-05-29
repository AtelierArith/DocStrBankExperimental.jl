```
SemiContinuousOffsetInvestment <: Investment
```

Semi-continuous investments, that is the added capacity is either zero or between a minimum and a maximum value. In this subtype, the cost is not crossing the origin. Instead, there is an offset (y- intercept) in the variable `capex_cap`, that is its value is larger or smaller than 0 at an invested capacity of 0 given by the field `capex_offset`. This allows to the user to use different slopes, and hence, account for economy of scales.

Semi-continuous investments introduce one binary variable for each investment period.

# Fields

  * **`max_add::TimeProfile`** is the maximum added capacity in an investment period.
  * **`min_add::TimeProfile`** is the minimum added capacity in an investment period. In the case of `SemiContinuousOffsetInvestment`, this implies that the model **must** invest at least in this capacity in each investment period. in this capacity in each investment period where the model decides to invest. The model can also choose not too invest at all.
  * **`capex_offset::TimeProfile`** is offset for the CAPEX in an investment period.
