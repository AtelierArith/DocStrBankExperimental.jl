```
construct_diff_version(f, g) -> pass_trough_function
```

Constructs a pass trough function for the given function `f` and gradient function `g`. The pass trough function is a function that returns the same value as `f` but the gradient is taken from `g`. Optional parameter k controls the steepnes of the gradient, default is 1. Supports both scalars and arrays.
