```
surrogate(x, method::Surrogate [, rng]) → s
```

Create a single surrogate timeseries `s` from `x` based on the given `method`. If you want to generate multiple surrogates from `x`, you should use [`surrogenerator`](@ref) for better performance.
