```julia
Prior_HorseShoe
```

Type representing the HorseShoe Prior.

*Prior model*

$$
\tau \sim HalfCauchy(0,1),
$$

$$
\lambda_j \sim HalfCauchy(0,1), j=1,2,\cdots,p
$$

$$
\sigma \sim HalfCauchy(0,1),
$$

$$
\alpha | \sigma,\tau \sim N(0,\tau *\sigma),
$$

$$
\beta_j | \sigma,\lambda_j ,\tau \sim Normal(0,\lambda_j *\tau *\sigma),
$$

*Likelihood or data model*

$$
\mu_i= \alpha + \mathbf{x}_i^T\beta
$$

$$
y_i \sim D(\mu_i,\sigma), i=1,2,\cdots,n
$$

**Note**:  $D()$ is appropriate distribution of $y_i$ based on the `modelClass`, where 

  * $\mathbf{E}(y_i)=g(\mu_i)$,
  * $Var(y_i)=\sigma^2$, and
  * $\beta$=($\beta_1,\beta_2,\cdots,\beta_p$)
