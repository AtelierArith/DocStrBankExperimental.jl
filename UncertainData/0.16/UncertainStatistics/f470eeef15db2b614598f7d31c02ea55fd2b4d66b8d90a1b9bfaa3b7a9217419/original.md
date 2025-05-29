```
ExactOneSampleKSTestElementWise(ud::UncertainDataset,
    d::UnivariateDistribution, n::Int = 1000) -> Vector{ExactOneSampleKSTest}
```

First, draw `n` realisations of each uncertain value in `ud`, keeping one pool of values for each uncertain value.

Then, perform an element-wise (pool-wise) one-sample exact Kolmogorov–Smirnov test of the null hypothesis that each value pool comes from the distribution `d` against the alternative hypothesis that the sample is not drawn from `d`.
