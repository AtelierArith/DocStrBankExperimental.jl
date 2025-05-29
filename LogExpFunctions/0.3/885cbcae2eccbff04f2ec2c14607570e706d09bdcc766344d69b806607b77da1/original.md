```julia
logabssinh(x)

```

Return `log(abs(sinh(x)))`, carefully evaluated without intermediate calculation of `sinh(x)`.

The implementation ensures `logabssinh(-x) = logabssinh(x)`.
