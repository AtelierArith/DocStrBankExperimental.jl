```
ribbonplot(x,y,[q=0.025]; N=true)
```

Plots a vector of particles with a ribbon covering quantiles `q, 1-q`. If `q::Tuple`, then you can specify both lower and upper quantile, e.g., `(0.01, 0.99)`.

If a positive number `N` is provided, `N` sample trajectories will be plotted on top of the ribbon.
