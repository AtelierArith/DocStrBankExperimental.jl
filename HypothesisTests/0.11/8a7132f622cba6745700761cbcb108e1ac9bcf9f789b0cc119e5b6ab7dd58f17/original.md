```
CorrelationTest(x, y)
```

Perform a t-test for the hypothesis that $\text{Cor}(x,y) = 0$, i.e. the correlation  of vectors `x` and `y` is zero.

```
CorrelationTest(x, y, Z)
```

Perform a t-test for the hypothesis that $\text{Cor}(x,y|Z=z) = 0$, i.e. the partial correlation of vectors `x` and `y` given the matrix `Z` is zero.

Implements `pvalue` for the t-test. Implements `confint` using an approximate confidence interval based on Fisher's $z$-transform.

See also `partialcor` from StatsBase.

# External resources

  * [Partial correlation on Wikipedia](https://en.wikipedia.org/wiki/Partial_correlation#As_conditional_independence_test) (for the construction of the confidence interval)
  * [Section testing using Student's t-distribution from Pearson correlation coefficient on Wikipedia](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient#Testing_using_Student's_t-distribution)
  * [K.J. Levy and S.C. Narula (1978): Testing Hypotheses concerning Partial Correlations: Some Methods and Discussion. International Statistical Review 46(2).](https://www.jstor.org/stable/1402814)
