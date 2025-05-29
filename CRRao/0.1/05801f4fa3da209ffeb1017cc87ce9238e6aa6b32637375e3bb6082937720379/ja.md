```julia
Prior_Gauss
```

ガウス事前分布を表す型。ユーザーは線形回帰モデルのために特定の事前平均と標準偏差を持ち、$\alpha$ と $\beta$ を指定します。

*事前モデル*

$$
\sigma \sim InverseGamma(a_0,b_0),
$$

$$
\alpha | \sigma,v \sim Normal(\alpha_0,\sigma_{\alpha_0}),
$$

$$
\beta | \sigma,v \sim Normal_p(\beta_0,\sigma_{\beta_0}),
$$

*尤度またはデータモデル*

$$
\mu_i= \alpha + \mathbf{x}_i^T\beta
$$

$$
y_i \sim N(\mu_i,\sigma),
$$

**注意**: $N()$ は $y_i$ のガウス分布であり、 

  * $$
    \mathbf{E}(y_i)=g(\mu_i)
    $$

    、および
  * $$
    Var(y_i)=\sigma^2
    $$

    。
