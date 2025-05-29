```
FlignerKilleenTest(groups)
FlignerKilleenTest(groups::AbstractVector{<:Real}...)
```

Perform Fligner-Killeen median test of the null hypothesis that the `groups` have equal variances, a test for homogeneity of variances.

This test is most robust against departures from normality, see references. It is a $k$-sample simple linear rank method that uses the ranks of the absolute values of the centered samples and weights

$$
a_{N,i} = \Phi^{-1}(1/2 + (i/2(N+1)))
$$

The version implemented here uses median centering in each of the samples.

Implements: [`pvalue`](@ref)

# References

  * Conover, W. J., Johnson, M. E., Johnson, M. M., A comparative study of tests for homogeneity of variances, with applications to the outer continental shelf bidding data. Technometrics, 23, 351–361, 1980

# External links

  * [Fligner-Killeen test on Statistical Analysis Handbook ](https://www.statsref.com/HTML/index.html?fligner-killeen_test.html)
