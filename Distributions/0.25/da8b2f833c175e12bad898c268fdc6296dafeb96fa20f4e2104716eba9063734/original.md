```
fit(D, args...)
```

Fit a distribution of type `D` to `args`.

The fit function will choose a reasonable way to fit the distribution, which, in most cases, is maximum likelihood estimation. Note that this algorithm may change; for a function that will behave consistently across versions, see  `fit_mle`.

By default, the fallback is [`fit_mle(D, args...)`](@ref); developers can change this default for a specific distribution type `D <: Distribution` by defining a `fit(::Type{D}, args...)` method.
