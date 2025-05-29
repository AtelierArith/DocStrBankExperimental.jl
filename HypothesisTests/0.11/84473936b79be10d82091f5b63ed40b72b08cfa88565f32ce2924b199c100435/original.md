```
LeveneTest(groups; scorediff=abs, statistic=mean)
LeveneTest(groups::AbstractVector{<:Real}...; scorediff=abs, statistic=mean)
```

Perform Levene's test of the hypothesis that that the `groups` variances are equal. By default the mean `statistic` is used for centering in each of the `groups`, but other statistics are accepted: median or truncated mean, see [`BrownForsytheTest`](@ref). By default the absolute value of the score difference, `scorediff`, is used, but other functions are accepted: x² or √|x|.

The test statistic, $W$, is equivalent to the $F$ statistic, and is defined as follows:

$$
W = \frac{(N-k)}{(k-1)} \cdot \frac{\sum_{i=1}^k N_i (Z_{i\cdot}-Z_{\cdot\cdot})^2}
    {\sum_{i=1}^k \sum_{j=1}^{N_i} (Z_{ij}-Z_{i\cdot})^2},
$$

where

  * $k$ is the number of different groups to which the sampled cases belong,
  * $N_i$ is the number of cases in the $i$th group,
  * $N$ is the total number of cases in all groups,
  * $Y_{ij}$ is the value of the measured variable for the $j$th case from the $i$th group,
  * $Z_{ij} = |Y_{ij} - \bar{Y}_{i\cdot}|$, $\bar{Y}_{i\cdot}$ is a mean of the  $i$th group,
  * $Z_{i\cdot} = \frac{1}{N_i} \sum_{j=1}^{N_i} Z_{ij}$ is the mean of the $Z_{ij}$ for group $i$,
  * $Z_{\cdot\cdot} = \frac{1}{N} \sum_{i=1}^k \sum_{j=1}^{N_i} Z_{ij}$ is the mean of all $Z_{ij}$.

The test statistic $W$ is approximately $F$-distributed with $k-1$ and $N-k$ degrees of freedom.

Implements: [`pvalue`](@ref)

# References

  * Levene, Howard, "Robust tests for equality of variances".  In Ingram Olkin; Harold Hotelling; et al. (eds.).  Contributions to Probability and Statistics: Essays in Honor of Harold Hotelling.  Stanford University Press. pp. 278–292, 1960

# External links

  * [Levene's test on Wikipedia ](https://en.wikipedia.org/wiki/Levene%27s_test)
