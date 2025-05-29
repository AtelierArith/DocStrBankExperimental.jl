```
OneSampleTTest(d1::AbstractUncertainValue,
                d2::AbstractUncertainValue,
                n::Int = 1000; μ0::Real=0) -> OneSampleTTest
```

Perform a paired sample t-test of the null hypothesis that the differences between pairs of uncertain values in `d1` and `d2` come from a distribution with mean `μ0` against the alternative hypothesis that the distribution does not have mean `μ0`.
