```
PositivityPreservingLimiterZhangShu(; threshold, variables)
```

The fully-discrete positivity-preserving limiter of

  * Zhang, Shu (2011) Maximum-principle-satisfying and positivity-preserving high-order schemes for conservation laws: survey and new developments [doi: 10.1098/rspa.2011.0153](https://doi.org/10.1098/rspa.2011.0153)

The limiter is applied to all scalar `variables` in their given order using the associated `thresholds` to determine the minimal acceptable values. The order of the `variables` is important and might have a strong influence on the robustness.
