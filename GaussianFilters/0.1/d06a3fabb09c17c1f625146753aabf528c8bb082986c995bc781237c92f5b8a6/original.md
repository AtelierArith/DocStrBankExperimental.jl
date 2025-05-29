```
multiple_target_state_extraction(b::GaussianMixture, th::Real)
```

Extracts targets whose weights (x.w) are above threshold.

Arguments:     `b::GaussianMixture`: Set of Gaussian Mixtures     `th::Real`: Threshold on weights. Above this threshold,     state estimate is extracted

Returns:     X: Multi-Target State Estimate
