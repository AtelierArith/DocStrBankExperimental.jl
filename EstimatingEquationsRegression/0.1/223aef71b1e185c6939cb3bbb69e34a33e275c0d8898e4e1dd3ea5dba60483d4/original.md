```
fit(GeneralizedEstimatingEquationsModel, X, y, g, l, v, [c = IndependenceCor()]; <keyword arguments>)
```

Fit a generalized linear model to data using generalized estimating equations (GEE).  This interface emphasizes the "quasi-likelihood" framework for GEE and requires direct specification of the link and variance function, without reference to any distribution/family.
