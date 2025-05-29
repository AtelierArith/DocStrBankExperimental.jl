```
throw_if_containsnan(r, f, args)
```

Utility function that checks if a value `r`, assumed to be the result of `f(args...)`, contains `NaN` values and if so, throws an `ReturnValueContainsNaN` exception.

`throw_if_containsnan` comes with an specialized `ChainRulesCore.rrule` to avoid computational overhead during automatic differentiation.
