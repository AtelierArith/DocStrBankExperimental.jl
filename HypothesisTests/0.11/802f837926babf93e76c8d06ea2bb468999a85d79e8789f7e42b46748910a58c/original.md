```
KSampleADTest(xs::AbstractVector{<:Real}...; modified = true, nsim = 0)
```

Perform a $k$-sample Anderson–Darling test of the null hypothesis that the data in the $k$ vectors `xs` come from the same distribution against the alternative hypothesis that the samples come from different distributions.

`modified` parameter enables a modified test calculation for samples whose observations do not all coincide.

If `nsim` is equal to 0 (the default) the asymptotic calculation of p-value is used. If it is greater than 0, an estimation of p-values is used by generating `nsim` random splits of the pooled data on $k$ samples, evaluating the AD statistics for each split, and computing the proportion of simulated values which are greater or equal to observed. This proportion is reported as p-value estimate.

Implements: [`pvalue`](@ref)

# References

  * F. W. Scholz and M. A. Stephens, K-Sample Anderson-Darling Tests, Journal of the American Statistical Association, Vol. 82, No. 399. (Sep., 1987), pp. 918-924.
