```
ChaoShen <: DiscreteInfoEstimatorShannon
ChaoShen(definition::Shannon = Shannon())
```

The `ChaoShen` estimator is used with [`information`](@ref) to compute the discrete [`Shannon`](@ref) entropy according to [Chao2003](@citet).

## Description

This estimator is a modification of the [`HorvitzThompson`](@ref) estimator that multiplies each plugin probability estimate by an estimate of sample coverage. If $f_1$ is the number of singletons (outcomes that occur only once) in a sample of length $N$, then the sample coverage is $C = 1 - \dfrac{f_1}{N}$. The Chao-Shen estimator of Shannon entropy is then

$$
H_S^{CS} = -\sum_{i=1}^M \left( \dfrac{C p_i \log(C p_i)}{1 - (1 - C p_i)^N} \right),
$$

where $N$ is the sample size and $M$ is the number of [`outcomes`](@ref). If $f_1 = N$, then $f_1$ is set to $f_1 = N - 1$ to ensure positive entropy [Arora2022](@cite).
