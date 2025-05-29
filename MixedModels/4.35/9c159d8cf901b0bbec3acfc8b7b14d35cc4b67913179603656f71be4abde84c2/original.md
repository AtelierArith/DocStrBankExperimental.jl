```
replicate(f::Function, n::Integer; progress=true)
```

Return a vector of the values of `n` calls to `f()` - used in simulations where the value of `f` is stochastic.

`progress` controls whether the progress bar is shown. Note that the progress bar is automatically disabled for non-interactive (i.e. logging) contexts.
