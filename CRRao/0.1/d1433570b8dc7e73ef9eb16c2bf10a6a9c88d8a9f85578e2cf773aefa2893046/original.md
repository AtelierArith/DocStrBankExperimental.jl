```julia
Prior_Cauchy
```

Type representing the Cauchy Prior.

*Prior model*

$$
\sigma \sim Half-Cauchy(0,1),
$$

$$
\alpha | \sigma \sim  Cauchy(0,\sigma),
$$

$$
\beta | \sigma \sim Cauchy(0,v*\sigma),
$$

*Likelihood or data model*

$$
\mu_i= \alpha + \mathbf{x}_i^T\beta
$$

$$
y_i \sim D(\mu_i,\sigma),
$$

**Note**: $D()$ is appropriate distribution of $y_i$ based on the `modelClass`, where 

  * $\mathbf{E}(y_i)=g(\mu_i)$, and
  * $Var(y_i)=\sigma^2$.
