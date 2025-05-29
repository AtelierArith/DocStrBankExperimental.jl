```
tf_enable_nan_injection(n_inject::Int)
```

Turn on NaN injection and injection `n_inject` NaNs. Does not modify odds, function and library lists, or recording/replay state.

```
tf_enable_nan_injection(; odds::Int = 10, n_inject::Int = 1, functions::Array{FunctionRef} = [], libraries::Array{String} = [])
```

Turn on NaN injection. Optionally configure the odds for injection, as well as the number of NaNs to inject, and the functions/libraries in which to inject NaNs. Overrides unspecified arguments to their defaults.
