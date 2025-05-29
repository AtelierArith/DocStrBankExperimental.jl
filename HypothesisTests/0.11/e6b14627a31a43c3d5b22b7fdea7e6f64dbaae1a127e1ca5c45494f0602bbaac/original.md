```
FisherExactTest(a::Integer, b::Integer, c::Integer, d::Integer)
```

Perform Fisher's exact test of the null hypothesis that the success probabilities $a/c$ and $b/d$ are equal, that is the odds ratio $(a/c) / (b/d)$ is one, against the alternative hypothesis that they are not equal.

See [`pvalue(::FisherExactTest)`](@ref) and [`confint(::FisherExactTest)`](@ref) for details about the computation of the default p-value and confidence interval, respectively.

The contingency table is structured as:

|  -   | X1  | X2  |
|:----:|:---:|:---:|
| *Y1* |  a  |  b  |
| *Y2* |  c  |  d  |

!!! note
    The `show` function output contains the conditional maximum likelihood estimate of the odds ratio rather than the sample odds ratio; it maximizes the likelihood given by Fisher's non-central hypergeometric distribution.


Implements: [`pvalue(::FisherExactTest)`](@ref), [`confint(::FisherExactTest)`](@ref)

# References

  * Fay, M.P., Supplementary material to "Confidence intervals that match Fisher’s exact or Blaker’s exact tests". Biostatistics, Volume 11, Issue 2, 1 April 2010, Pages 373–374, [link](https://doi.org/10.1093/biostatistics/kxp050)
