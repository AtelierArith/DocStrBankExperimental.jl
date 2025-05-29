```
TsallisExtropy <: InformationMeasure
TsallisExtropy(; base = 2)
```

The Tsallis extropy [Xue2023](@cite).

## Description

`TsallisExtropy` is used with [`information`](@ref) to compute

$$
J_T(P) = k \dfrac{N - 1 - \sum_{i=1}^N ( 1 - p[i])^q}{q - 1}
$$

for a probability distribution $P = \{p_1, p_2, \ldots, p_N\}$, with the $\log$ at the given `base`. Alternatively, `TsallisExtropy` can be used with [`information_normalized`](@ref), which ensures that the computed extropy is on the interval $[0, 1]$ by normalizing to to the maximal Tsallis extropy, given by

$$
J_T(P) = \dfrac{(N - 1)N^{q - 1} - (N - 1)^q}{(q - 1)N^{q - 1}}
$$
