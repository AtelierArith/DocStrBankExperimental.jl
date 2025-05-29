```
@uncertain f(value ± stddev, ...)
```

A macro to calculate `f(value) ± uncertainty`, with `uncertainty` derived from `stddev` according to rules of linear error propagation theory.

Function `f` can accept any number of real arguments.
