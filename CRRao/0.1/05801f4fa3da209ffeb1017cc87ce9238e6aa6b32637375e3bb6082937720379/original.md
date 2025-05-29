```julia
Prior_Gauss
```

Type representing the Gaussian Prior. Users have specific  prior mean and standard deviation, for $\alpha$ and $\beta$  for linear regression model. 

*Prior model*

$$
\sigma \sim InverseGamma(a_0,b_0),
$$

$$
\alpha | \sigma,v \sim Normal(\alpha_0,\sigma_{\alpha_0}),
$$

$$
\beta | \sigma,v \sim Normal_p(\beta_0,\sigma_{\beta_0}),
$$

*Likelihood or data model*

$$
\mu_i= \alpha + \mathbf{x}_i^T\beta
$$

$$
y_i \sim N(\mu_i,\sigma),
$$

**Note**: $N()$ is Gaussian distribution of $y_i$, where 

  * $\mathbf{E}(y_i)=g(\mu_i)$, and
  * $Var(y_i)=\sigma^2$.
