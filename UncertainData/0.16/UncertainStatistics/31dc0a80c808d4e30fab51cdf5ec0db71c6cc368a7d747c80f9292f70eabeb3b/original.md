```
MannWhitneyUTest(d1::AbstractUncertainValue, d2::AbstractUncertainValue,
    n::Int = 1000) -> MannWhitneyUTest
```

Let `s1` and `s2` be samples of `n` realisations from the distributions furnishing the uncertain values `d1` and `d2`.

Perform a Mann-Whitney U test of the null hypothesis that the probability that an observation drawn from the same population as `s1` is greater than an observation drawn from the same population as `s2` is equal to the probability that an observation drawn from the same population as `s2` is greater than an observation drawn from the same population as `s1` against the alternative hypothesis that these probabilities are not equal.

The Mann-Whitney U test is sometimes known as the Wilcoxon rank-sum test. When there are no tied ranks and ≤50 samples, or tied ranks and ≤10 samples, `MannWhitneyUTest` performs an exact Mann-Whitney U test. In all other cases, `MannWhitneyUTest` performs an approximate Mann-Whitney U test.
