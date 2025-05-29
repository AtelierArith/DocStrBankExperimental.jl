```
DF2TFilter(coef[, si])
```

Construct a stateful direct form II transposed filter with coefficients `coef`. `si` is an optional array representing the initial filter state (defaults to zeros). If `f` is a `PolynomialRatio`, `Biquad`, or `SecondOrderSections`, filtering is implemented directly. If `f` is a `ZeroPoleGain` object, it is first converted to a `SecondOrderSections` object.
