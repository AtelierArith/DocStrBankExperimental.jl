```
plausible_limits(x::Num)
```

Return a tuple (min, max) of plausible limiting values for the variable `x`. If `x` is defined with the `bounds` metadata, this is returned as the limits. Else, if `x` has a default value, the limits are this value ± 20%. Else, if there is no default value, an error is thrown.
