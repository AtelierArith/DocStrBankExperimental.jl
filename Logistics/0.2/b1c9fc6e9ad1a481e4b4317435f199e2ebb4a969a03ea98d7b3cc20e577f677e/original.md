```
logitexp(x::Real)
```

Return `logit(exp(x))` evaluated carefully without intermediate calculation  of `exp(x)`.

Its inverse is the [`loglogistic`](@ref) function.
