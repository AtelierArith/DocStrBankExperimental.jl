```
quadpoints(refspace, charts, rules)
```

Computed a matrix of vectors containing (weight, point, value) triples that can be used in numerical integration over the elements described by the charts. Internally, this method used `quadpoints(chart, rule)` to retrieve the points and weights for a certain quadrature rule over `chart`.
