```
partialresponse(model::T, i::Integer, j::Integer, s::Tuple=(50, 50); inflated::Bool, kwargs...)
```

This method returns the partial response of applying the trained model to a simulated dataset where all variables *except* `i` and `j` are set to their mean value.

This function will return a grid corresponding to evenly spaced values of `i` and `j`, the size of which is given by the last argument `s` (defaults to 50 × 50).

All keyword arguments are passed to `predict`.
