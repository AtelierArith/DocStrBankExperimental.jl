```
integrate(a, [x])
```

Return the integral of `a::Taylor1`. The constant of integration (0-th order coefficient) is set to `x`, which is zero if omitted. Note that the order of the result is `a.order+1`.
