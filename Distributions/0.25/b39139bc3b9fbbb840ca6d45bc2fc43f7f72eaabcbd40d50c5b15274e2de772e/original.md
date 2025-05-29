```
FDist(ν1, ν2)
```

The *F distribution* has probability density function

$$
f(x; \nu_1, \nu_2) = \frac{1}{x B(\nu_1/2, \nu_2/2)}
\sqrt{\frac{(\nu_1 x)^{\nu_1} \cdot \nu_2^{\nu_2}}{(\nu_1 x + \nu_2)^{\nu_1 + \nu_2}}}, \quad x>0
$$

It is related to the [`Chisq`](@ref) distribution via the property that if $X_1 \sim \operatorname{Chisq}(\nu_1)$ and $X_2 \sim \operatorname{Chisq}(\nu_2)$, then $(X_1/\nu_1) / (X_2 / \nu_2) \sim \operatorname{FDist}(\nu_1, \nu_2)$.

```julia
FDist(ν1, ν2)     # F-Distribution with parameters ν1 and ν2

params(d)         # Get the parameters, i.e. (ν1, ν2)
```

External links

  * [F distribution on Wikipedia](http://en.wikipedia.org/wiki/F-distribution)
