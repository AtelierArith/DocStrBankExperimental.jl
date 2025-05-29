```
Shannon <: InformationMeasure
Shannon(; base = 2)
```

The Shannon [Shannon1948](@cite) entropy, used with [`information`](@ref) to compute:

$$
H(p) = - \sum_i p[i] \log(p[i])
$$

with the $\log$ at the given `base`.

The maximum value of the Shannon entropy is $\log_{base}(L)$, which is the entropy of the uniform distribution with $L$ the [`total_outcomes`](@ref).
