```
randst(rng, d::Distributions.Sampleable; kwargs...)
```

When no keyword arguments are provided, `randst` behaves identically to `rand(rng, d)` in both ordinary computation and for stochastic triple dispatches. However, `randst` also allows the user to provide various keyword arguments for customizing the differentiation logic. The set of allowed keyword arguments depends on the type of `d`: a couple common ones are `derivative_coupling` and `propagation_coupling`.

For developers: if you wish to accept custom keyword arguments in a stochastic triple dispatch, you should overload `randst`, and redirect `rand` to your `randst` method. If you do not, it suffices to just overload `rand`.
