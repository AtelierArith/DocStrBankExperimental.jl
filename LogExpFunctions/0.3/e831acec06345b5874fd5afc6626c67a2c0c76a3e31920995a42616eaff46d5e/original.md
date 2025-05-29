```julia
log1mlogistic(x)

```

Return `log(1 - logistic(x))`, computed more carefully and with fewer calls than the naive composition of functions.

Its inverse is the [`logit1mexp`](@ref) function.
