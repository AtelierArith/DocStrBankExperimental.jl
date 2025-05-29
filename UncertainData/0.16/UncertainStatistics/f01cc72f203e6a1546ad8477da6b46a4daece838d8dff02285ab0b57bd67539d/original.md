```
OneSampleTTest(d::AbstractUncertainValue, n::Int = 1000;
    μ0::Real = 0) -> OneSampleTTest
```

Perform a one sample t-test of the null hypothesis that the uncertain value has a distribution with mean `μ0` against the alternative hypothesis that its distribution does not have mean `μ0`. `n` indicates the number of draws during resampling.
