```
hlerp(f, to, grid, I...)
```

Interpolate a field `f` to location to using harmonic linear interpolation rule.

`rule(t, v0, v1) = 1/(1/v0 + t * (1/v1 - 1/v0))`
