```
yeojohnson(λ; atol=0)
yeojohnson(λ, x; atol=0)
```

$$
\begin{cases} ((x_i+1)^\lambda-1)/\lambda                      &  \text{if }\lambda \neq 0, y \geq 0 \\
               \log(y_i + 1)                                     &  \text{if }\lambda =     0, y \geq 0 \\
               -((-x_i + 1)^{(2-\lambda)} - 1) / (2 - \lambda)  &  \text{if }\lambda \neq 2, y <     0 \\
               -\log(-x_i + 1)                                   &  \text{if }\lambda =     2, y <     0
\end{cases}
$$

`atol` controls the absolute tolerance for treating λ as zero or two.

The one argument variant curries and creates a one-argument function of `x` for the given λ.

See also [`YeoJohnsonTransformation`](@ref).

# References

Yeo, I.-K., & Johnson, R. A. (2000). A new family of power transformations to improve normality or symmetry. Biometrika, 87(4), 954–959. https://doi.org/10.1093/biomet/87.4.954
