```
cauchy(x, s::IsotropicStrategy)
```

Performs isotropic mutation of the recombinant `x` given the strategy `s`  by adding a noise from the Cauchy distribution as follows:

  * $x_i^\prime = x_i + s.\sigma_i \delta_i$

where $\delta$ is a Cauchy random variable with the scale parameter $t = 1$ [^2].
