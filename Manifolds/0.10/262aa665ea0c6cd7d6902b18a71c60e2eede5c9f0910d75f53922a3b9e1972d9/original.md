```
change_representer(M::Hyperbolic, ::EuclideanMetric, p::PoincareBallPoint, X::PoincareBallTangentVector)
```

Since in the metric we have the term $α = \frac{2}{1-\sum_{i=1}^n p_i^2}$ per element, the correction for the gradient reads $Y = \frac{1}{α^2}X$.
