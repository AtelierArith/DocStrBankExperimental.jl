```
filt(f, x[, si])
```

Apply filter or filter coefficients `f` along the first dimension of array `x`. If `f` is a filter coefficient object, `si` is an optional array representing the initial filter state (defaults to zeros). If `f` is a `PolynomialRatio`, `Biquad`, or `SecondOrderSections`, filtering is implemented directly. If `f` is a `ZeroPoleGain` object, it is first converted to a `SecondOrderSections` object.  If `f` is a Vector, it is interpreted as an FIR filter, and a naïve or FFT-based algorithm is selected based on the data and filter length.
