```
MannWhitneyUTest(d1::UncertainDataset, d2::UncertainDataset,
    n::Int = 1000) -> Vector{MannWhitneyUTest}
```

Assume `d1` and `d2` consist of the same number of uncertain values. Let $s_{1_{i}}$ be a sample of `n` realisations of the distribution furnishing the uncertain value `d1[i]`, where $i \in [1, 2, \ldots, N]$ and $N$ is the number of uncertain values in `d1`. Let $s_{2_{i}}$ be the corresponding sample for `d2[i]`. This function

Perform an element-wise Mann-Whitney U test of the null hypothesis that the probability that an observation drawn from the same population as $s_{1_{i}}$ is greater than an observation drawn from the same population as $s_{2_{i}}$ is equal to the probability that an observation drawn from the same population as $s_{2_{i}}$ is greater than an observation drawn from the same population as $s_{1_{i}}$ against the alternative hypothesis that these probabilities are not equal.

The Mann-Whitney U test is sometimes known as the Wilcoxon rank-sum test. When there are no tied ranks and ≤50 samples, or tied ranks and ≤10 samples, `MannWhitneyUTest` performs an exact Mann-Whitney U test. In all other cases, `MannWhitneyUTest` performs an approximate Mann-Whitney U test.
