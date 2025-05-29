```
fit(::Type{BayesNet}, data, edges)
```

Fit a Bayesian Net whose variables are the columns in data and whose edges are given in edges

```
ex: fit(DiscreteBayesNet, data, (:A=>:B, :C=>B))
```
