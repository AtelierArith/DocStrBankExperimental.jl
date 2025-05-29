```
LSM <: AbstractPricingMethod
```

Least Squares Monte Carlo (LSM) pricing method for American options.

Uses regression to estimate continuation values and determine optimal stopping times.

# Fields

  * `mc_method`: A `MonteCarlo` method specifying dynamics and simulation strategy.
  * `degree`: Degree of the polynomial basis for regression.
