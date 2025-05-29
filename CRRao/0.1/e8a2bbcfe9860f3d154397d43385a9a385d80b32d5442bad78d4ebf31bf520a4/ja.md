```julia
Prior_Ridge
```

リッジプライヤを表す型。

*プライヤモデル*

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
