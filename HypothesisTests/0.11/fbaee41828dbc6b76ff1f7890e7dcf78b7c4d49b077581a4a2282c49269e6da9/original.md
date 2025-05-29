```
OneWayANOVATest(groups)
OneWayANOVATest(groups::AbstractVector{<:Real}...)
```

Perform one-way analysis of variance test of the hypothesis that that the `groups` means are equal.

The one-way analysis of variance (one-way ANOVA) is a technique that can be used to compare means of two or more samples. The ANOVA tests the null hypothesis, which states that samples in all groups are drawn from populations with the same mean values. To do this, two estimates are made of the population variance. The ANOVA produces an F-statistic, the ratio of the variance calculated among the means to the variance within the samples.

Implements: [`pvalue`](@ref)

# External links

  * [One-way analysis of variance on Wikipedia ](https://en.wikipedia.org/wiki/One-way_analysis_of_variance)
