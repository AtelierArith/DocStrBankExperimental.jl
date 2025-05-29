```julia
Prior_Ridge
```

Type representing the Ridge Prior.

*Prior model*

$$
v \sim InverseGamma(h,h),
$$

$$
\sigma \sim InverseGamma(a_0,b_0),
$$

$$
\alpha | \sigma,v \sim Normal(0,v*\sigma),
$$

$$
\beta | \sigma,v \sim Normal_p(0,v*\sigma),
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
