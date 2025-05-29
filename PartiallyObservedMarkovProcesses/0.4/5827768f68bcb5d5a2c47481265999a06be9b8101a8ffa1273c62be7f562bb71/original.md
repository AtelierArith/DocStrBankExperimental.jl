```
simulate_array(object; nsim = 1, params, rinit, rprocess, rmeasure, args...)
```

Simulate the POMP. At least the `rinit`, `rprocess`, and `rmeasure` basic components, are needed. Return an array containing the simulated sample paths.
