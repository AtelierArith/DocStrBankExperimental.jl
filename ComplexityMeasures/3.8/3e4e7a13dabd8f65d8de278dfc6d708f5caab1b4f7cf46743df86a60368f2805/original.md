```
HorvitzThompson <: DiscreteInfoEstimatorShannon
HorvitzThompson(measure::Shannon = Shannon())
```

The `HorvitzThompson` estimator is used with [`information`](@ref) to compute the discrete [`Shannon`](@ref) entropy according to [Horvitz1952](@citet).

# Description

The Horvitz-Thompson estimator of [`Shannon`](@ref) entropy is given by

$$
H_S^{HT} = -\sum_{i=1}^M \dfrac{p_i \log(p_i) }{1 - (1 - p_i)^N},
$$

where $N$ is the sample size and $M$ is the number of [`outcomes`](@ref). Given the true probability $p_i$ of the $i$-th outcome, $1 - (1 - p_i)^N$ is the probability that the outcome appears at least once in a sample of size $N$ [Arora2022](@cite). Dividing by this inclusion probability is a form of weighting, and compensates for situations where certain outcomes have so low probabilities that they are not often observed in a sample, for example in power-law distributions.
