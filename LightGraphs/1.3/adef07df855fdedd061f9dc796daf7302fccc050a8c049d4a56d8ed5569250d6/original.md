```
diffusion_rate(results)
diffusion_rate(g, p, n; ...)
```

Given the results of a `diffusion` output or the parameters to the `diffusion` simulation itself, (run and) return the rate of diffusion as a vector representing the cumulative number of vertices infected at each simulation step, restricted to vertices included in `watch`, if specified.
