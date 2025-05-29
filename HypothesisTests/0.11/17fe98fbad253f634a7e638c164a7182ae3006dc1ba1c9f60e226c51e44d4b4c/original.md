```
ClarkWestTest(e1::AbstractVector{<:Real}, e2::AbstractVector{<:Real}, lookahead::Integer=1)
```

Perform the Clark-West test of equal performance of two nested prediction models, in terms of the out-of-sample mean squared prediction errors.

`e1` is a vector of forecasts from the smaller (nested) model, `e2` is a vector of forecast errors from the larger model, and `lookahead` is the number of steps ahead of the forecast. Typically, the null hypothesis is that the two models perform equally well (a two-sided test), but sometimes we test whether the larger model performs better, which is indicated by a positive test statistic, for instance, above 1.645 for the 5% significance level (right tail test).

Implements: [`pvalue`](@ref)

# References

  * Clark, T. E., West, K. D. 2006, Using out-of-sample mean squared prediction errors to test the martingale difference hypothesis. Journal of Econometrics, 135(1): 155–186.
  * Clark, T. E., West, K. D. 2007, Approximately normal tests for equal predictive accuracy in nested models. Journal of Econometrics, 138(1): 291–311.
