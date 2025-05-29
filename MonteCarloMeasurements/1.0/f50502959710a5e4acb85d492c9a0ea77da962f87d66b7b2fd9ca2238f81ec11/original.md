```
errorbarplot(x,y,[q=0.025])
```

Plots a vector of particles with error bars at quantile `q`. If `q::Tuple`, then you can specify both lower and upper quantile, e.g., `(0.01, 0.99)`.
