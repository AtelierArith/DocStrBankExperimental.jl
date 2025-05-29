```
cooksdistance(obj::LinearModel)
```

Compute [Cook's distance](https://en.wikipedia.org/wiki/Cook%27s_distance) for each observation in linear model `obj`, giving an estimate of the influence of each data point. Currently only implemented for linear models without weights.
