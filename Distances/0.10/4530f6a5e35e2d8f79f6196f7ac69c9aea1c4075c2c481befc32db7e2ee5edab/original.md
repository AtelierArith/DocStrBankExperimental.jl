```
MinkowskiMetric <: Metric
```

A Minkowski metric is a metric that is defined by the formula:

`d(x, y) = sum(w .* (x - y) .^ p) ^ (1 / p)`

where the `p` parameter defines the metric  and `w` is a potential weight vector (all 1's by default).

Common Minkowski metrics:

  * `Cityblock`/`WeightedCityblock`: Minkowski metric with `p=1`;
  * `Euclidean`/`WeightedEuclidean`: Minkowski metric with `p=2`;
  * `Chebyshev`: Limit of `d` as `p` approaches infinity;
  * `Minkowski`/`WeightedMinkowski`: generic Minkowski metric for any `p`.

## Notes

  * The difference between `Minkowski`/`WeightedMinkowski` and `MinkowskiMetric`  is that while the first are generic Minkowski metrics,  the second is the parent type of these metrics.
