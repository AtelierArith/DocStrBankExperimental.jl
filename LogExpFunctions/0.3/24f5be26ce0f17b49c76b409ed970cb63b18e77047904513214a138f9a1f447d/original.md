```julia
logitexp(x)

```

Return `logit(exp(x))`, computed more carefully and with fewer calls than the naive composition of functions.

Its inverse is the [`loglogistic`](@ref) function.
