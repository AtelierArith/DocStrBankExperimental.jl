```
OneSampleTTestPooled(d1::UncertainDataset,
    d2::UncertainDataset,
    n::Int = 1000; μ0::Real = 0) -> OneSampleTTest
```

First, sample `n` draws of each uncertain value in each dataset, pooling the draws from the elements of `d1` and the draws from the elements of `d2` separately. Then, perform a paired sample t-test of the null hypothesis that the differences between pairs of uncertain values in `d1` and `d2` come from a distribution with mean `μ0` against the alternative hypothesis that the distribution does not have mean `μ0`.
