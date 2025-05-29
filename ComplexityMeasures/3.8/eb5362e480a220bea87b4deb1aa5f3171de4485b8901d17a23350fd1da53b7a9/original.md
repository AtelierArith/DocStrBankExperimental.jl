```
Kaniadakis <: InformationMeasure
Kaniadakis(; κ = 1.0, base = 2.0)
```

The Kaniadakis entropy [Tsallis2009](@cite), used with [`information`](@ref) to compute

$$
H_K(p) = -\sum_{i=1}^N p_i f_\kappa(p_i),
$$

$$
f_\kappa (x) = \dfrac{x^\kappa - x^{-\kappa}}{2\kappa},
$$

where if $\kappa = 0$, regular logarithm to the given `base` is used, and 0 probabilities are skipped.
