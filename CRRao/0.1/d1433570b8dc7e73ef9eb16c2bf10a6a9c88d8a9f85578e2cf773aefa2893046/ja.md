```julia
Prior_Cauchy
```

Cauchy事前分布を表す型。

*事前モデル*

$$
\sigma \sim Half-Cauchy(0,1),
$$

$$
\alpha | \sigma \sim  Cauchy(0,\sigma),
$$

$$
\beta | \sigma \sim Cauchy(0,v*\sigma),
$$

*尤度またはデータモデル*

$$
\mu_i= \alpha + \mathbf{x}_i^T\beta
$$

$$
y_i \sim D(\mu_i,\sigma),
$$

**注意**: $D()$は`modelClass`に基づく$y_i$の適切な分布であり、 

  * $$
    \mathbf{E}(y_i)=g(\mu_i)
    $$

    、および
  * $$
    Var(y_i)=\sigma^2
    $$

    。
