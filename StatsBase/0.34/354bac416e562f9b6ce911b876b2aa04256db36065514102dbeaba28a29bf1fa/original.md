```
AnalyticWeights(vs, wsum=sum(vs))
```

Construct an `AnalyticWeights` vector with weight values `vs`. A precomputed sum may be provided as `wsum`.

Analytic weights describe a non-random relative importance (usually between 0 and 1) for each observation. These weights may also be referred to as reliability weights, precision weights or inverse variance weights. These are typically used when the observations being weighted are aggregate values (e.g., averages) with differing variances.
