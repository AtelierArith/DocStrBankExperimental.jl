```
partialresponse(model::T, i::Integer, args...; inflated::Bool, kwargs...)
```

This method returns the partial response of applying the trained model to a simulated dataset where all variables *except* `i` are set to their mean value. The `inflated` keywork, when set to `true`, will instead pick a random value within the range of the observations.

The different arguments that can follow the variable position are

  * nothing, where the unique values for the `i`-th variable are used (sorted)
  * a number, in which point that many evenly spaced points within the range of the variable are used
  * an array, in which case each value of this array is evaluated

All keyword arguments are passed to `predict`.
