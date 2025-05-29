```
lpc(x::AbstractVector, p::Int, [LPCBurg()])
```

Given input signal `x` and prediction order `p`, returns IIR coefficients `a` and average reconstruction error `prediction_err`. Note that this method does NOT return the leading `1` present in the true autocorrelative estimate; it omits it as it is implicit in every LPC estimate, and must be manually reintroduced if the returned vector should be treated as a polynomial.

The algorithm used is determined by the last optional parameter, and can be either `LPCBurg` or `LPCLevinson`.
