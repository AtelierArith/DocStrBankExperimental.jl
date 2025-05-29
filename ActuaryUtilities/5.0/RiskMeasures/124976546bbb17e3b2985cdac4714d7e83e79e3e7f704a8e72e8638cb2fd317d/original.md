```
DualPower(v)::RiskMeasure
DualPower(v)(risk)::T (where T is the type of values sampled in risk)
```

The Dual Power distortion risk measure is defined as $1 - (1 - x)^v$, where x is the cumulative distribution function (CDF) of the risk distribution and v is a positive parameter. risk can be a univariate distribution or an array of outcomes.

DualPower(v) returns a functor which can then be called on a risk distribution.
