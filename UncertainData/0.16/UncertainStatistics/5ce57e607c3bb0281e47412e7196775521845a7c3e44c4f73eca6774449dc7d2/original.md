```
MannWhitneyUTest(d1::UncertainDataset, d2::UncertainDataset,
    n::Int = 1000) -> MannWhitneyUTest
```

Let $s_{1_{i}}$ be a sample of `n` realisations of the distribution furnishing the uncertain value `d1[i]`, where $i \in [1, 2, \ldots, N]$ and $N$ is the number of uncertain values in `d1`.  Next, gather the samples for all $s_{1_{i}}$ in a pooled sample $S_1$.  Do the same for the second uncertain dataset `d2`, yielding the pooled sample  $S_2$.

Perform a Mann-Whitney U test of the null hypothesis that the probability that an observation drawn from the same population as $S_1$ is greater than an observation drawn from the same population as $S_2$ is equal to the probability that an observation drawn from the same population as $S_2$ is greater than an observation drawn from the same population as $S_1$ against the alternative hypothesis that these probabilities are not equal.

The Mann-Whitney U test is sometimes known as the Wilcoxon rank-sum test. When there are no tied ranks and ≤50 samples, or tied ranks and ≤10 samples, `MannWhitneyUTest` performs an exact Mann-Whitney U test. In all other cases, `MannWhitneyUTest` performs an approximate Mann-Whitney U test.
