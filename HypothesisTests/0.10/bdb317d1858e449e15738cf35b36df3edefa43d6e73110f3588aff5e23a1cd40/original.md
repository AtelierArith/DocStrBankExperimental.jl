```
confint(test::BinomialTest; level = 0.95, tail = :both, method = :clopper_pearson)
```

Compute a confidence interval with coverage `level` for a binomial proportion using one of the following methods. Possible values for `method` are:

  * `:clopper_pearson` (default): Clopper-Pearson interval is based on the binomial distribution. The empirical coverage is never less than the nominal coverage of `level`; it is usually too conservative.
  * `:wald`: Wald (or normal approximation) interval relies on the standard approximation of the actual binomial distribution by a normal distribution. Coverage can be erratically poor for success probabilities close to zero or one.
  * `:wilson`: Wilson score interval relies on a normal approximation. In contrast to `:wald`, the standard deviation is not approximated by an empirical estimate, resulting in good empirical coverages even for small numbers of draws and extreme success probabilities.
  * `:jeffrey`: Jeffreys interval is a Bayesian credible interval obtained by using a non-informative Jeffreys prior. The interval is very similar to the Wilson interval.
  * `:agresti_coull`: Agresti-Coull interval is a simplified version of the Wilson interval; both are centered around the same value. The Agresti Coull interval has higher or equal coverage.
  * `:arcsine`: Confidence interval computed using the arcsine transformation to make $var(p)$ independent of the probability $p$.

# References

  * Brown, L.D., Cai, T.T., and DasGupta, A. Interval estimation for a binomial proportion. Statistical Science, 16(2):101–117, 2001.

# External links

  * [Binomial confidence interval on Wikipedia](https://en.wikipedia.org/wiki/ Binomial_proportion_confidence_interval)
