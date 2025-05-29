```
ApproximateTwoSampleKSTestPooled(d1::UncertainDataset,
    d2::UncertainDataset, n::Int = 1000) -> ApproximateTwoSampleKSTest
```

First, draw `n` realisations of each uncertain value in `d1`, then separately draw `n` realisations of each uncertain value in `d2`. Then, pool all realisations for `d1` together and all realisations of `d2` together.

On the pooled realisations, perform an asymptotic two-sample Kolmogorov–Smirnov-test of the null hypothesis that the distribution furnishing the `d1` value pool represents the same distribution as the distribution furnishing the `d2` value pool, against the alternative hypothesis that the furnishing distributions are different.
