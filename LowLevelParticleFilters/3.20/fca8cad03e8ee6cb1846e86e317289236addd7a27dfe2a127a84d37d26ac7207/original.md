```
weighted_quantile(x,we,q)
weighted_quantile(sol,q)
```

Calculated weighted quantile `q` of particle trajectories. `we` are expweights. Returns a vector of length `size(x, 2)` where each entry has length `nx`. For a particle-filtering solution, this means the vector will be as long as the number of time steps in the solution.
