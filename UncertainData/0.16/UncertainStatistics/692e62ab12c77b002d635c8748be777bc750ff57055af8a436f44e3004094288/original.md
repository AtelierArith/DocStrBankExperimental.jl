```
OneSampleTTestPooled(d::UncertainDataset, n::Int = 1000;
    μ0::Real=0) -> OneSampleTTest
```

First, sample `n` draws of each uncertain value in `d1`, then pooling the draws together. Then, perform a one sample t-test of the null hypothesis that the uncertain values have a pooled distribution with mean `μ0` against the alternative hypothesis that its pooled distribution does not have mean `μ0`. `n` indicates the number of draws during resampling.
