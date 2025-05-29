```julia
logcosh(x)

```

Return `log(cosh(x))`, carefully evaluated without intermediate calculation of `cosh(x)`.

The implementation ensures `logcosh(-x) = logcosh(x)`.
