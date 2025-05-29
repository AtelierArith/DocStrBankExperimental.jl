```julia
logit1mexp(x)

```

Return `logit(1 - exp(x))`, computed more carefully and with fewer calls than the naive composition of functions.

Its inverse is the [`log1mlogistic`](@ref) function.
