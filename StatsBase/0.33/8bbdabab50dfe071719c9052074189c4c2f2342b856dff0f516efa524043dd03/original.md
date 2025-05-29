```
sem(x; mean=nothing)
sem(x::AbstractArray[, weights::AbstractWeights]; mean=nothing)
```

Return the standard error of the mean for a collection `x`. A pre-computed `mean` may be provided.

When not using weights, this is the (sample) standard deviation divided by the sample size. If weights are used, the  variance of the sample mean is calculated as follows:

  * `AnalyticWeights`: Not implemented.
  * `FrequencyWeights`: $\frac{\sum_{i=1}^n w_i (x_i - \bar{x_i})^2}{(\sum w_i) (\sum w_i - 1)}$
  * `ProbabilityWeights`: $\frac{n}{n-1} \frac{\sum_{i=1}^n w_i^2 (x_i - \bar{x_i})^2}{\left( \sum w_i \right)^2}$

The standard error is then the square root of the above quantities.

# References

Carl-Erik Särndal, Bengt Swensson, Jan Wretman (1992). Model Assisted Survey Sampling. New York: Springer. pp. 51-53.
