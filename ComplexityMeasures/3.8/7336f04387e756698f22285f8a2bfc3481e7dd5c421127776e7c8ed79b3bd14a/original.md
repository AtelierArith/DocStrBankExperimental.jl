```
RenyiExtropy <: InformationMeasure
RenyiExtropy(; q = 1.0, base = 2)
```

The Rényi extropy [Liu2023](@cite).

## Description

`RenyiExtropy` is used with [`information`](@ref) to compute

$$
J_R(P) = \dfrac{-(n - 1) \log{(n - 1)} + (n - 1) \log{ \left( \sum_{i=1}^N {(1 - p[i])}^q \right)} }{q - 1}
$$

for a probability distribution $P = \{p_1, p_2, \ldots, p_N\}$, with the $\log$ at the given `base`. Alternatively, `RenyiExtropy` can be used with [`information_normalized`](@ref), which ensures that the computed extropy is on the interval $[0, 1]$ by normalizing to to the maximal Rényi extropy, given by

$$
J_R(P) = (N - 1)\log \left( \dfrac{n}{n-1} \right) .
$$
