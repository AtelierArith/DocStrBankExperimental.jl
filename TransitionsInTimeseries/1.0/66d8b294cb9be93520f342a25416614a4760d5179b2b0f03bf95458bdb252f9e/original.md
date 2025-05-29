```
SlopeChangeSignificance(; moe_slope, moe_offset, slope_diff = moe_slope, pvalue = 0.05)
```

Test whether the result of [`SlopeChangeResults`](@ref) is statistically significant.

Two tests are done:

1. Check whether the *margin of error* of the fitted parameters `a, b, c, d` of the two linear segments `a + b*t, c + d*t` is less than the specified margins of error, for a chosen `pvalue`.
2. Test that the two slopes `b, d` have difference greater than `slope_diff`.

The Boolean `&` of the above two is the final test.

The margin of error is simply half the size of the confidence interval, also known as radius of the confidence interval.
