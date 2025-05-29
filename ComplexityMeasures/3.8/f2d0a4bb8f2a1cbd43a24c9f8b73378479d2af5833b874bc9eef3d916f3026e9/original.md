```
ShannonExtropy <: InformationMeasure
ShannonExtropy(; base = 2)
```

The Shannon extropy [Lad2015](@cite), used with [`information`](@ref) to compute

$$
J(x) = -\sum_{i=1}^N (1 - p[i]) \log{(1 - p[i])},
$$

for a probability distribution $P = \{p_1, p_2, \ldots, p_N\}$, with the $\log$ at the given `base`.
