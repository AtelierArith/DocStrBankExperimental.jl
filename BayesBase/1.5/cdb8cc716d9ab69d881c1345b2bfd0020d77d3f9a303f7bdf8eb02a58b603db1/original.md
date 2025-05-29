```
clamplog(x)
```

Same as `log` but clamps the input argument `x` to be in the range `tiny <= x <= typemax(x)` such that `log(0)` does not explode.
