```
simulate(object; nsim = 1, params, rinit, rprocess, rmeasure, args...)
```

Simulate the POMP. Returns an array of *PompObject*s. At least the `rinit`, `rprocess`, and `rmeasure` basic components, are needed.
