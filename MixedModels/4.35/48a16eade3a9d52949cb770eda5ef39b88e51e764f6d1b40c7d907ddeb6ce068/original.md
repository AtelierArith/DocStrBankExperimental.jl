```
shortestcovint(bsamp::MixedModelFitCollection, level = 0.95)
```

Return the shortest interval containing `level` proportion for each parameter from `bsamp.allpars`.

!!! warning
    Currently, correlations that are systematically zero are included in the the result. This may change in a future release without being considered a breaking change.

