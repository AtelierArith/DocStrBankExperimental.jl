```julia
Prior_TDist
```

T分布事前分布を表す型。

*事前モデル*

$$
v \sim InverseGamma(h,h),
$$

$$
\sigma \sim InverseGamma(a_0,b_0),
$$

$$
\alpha | \sigma,v \sim \sigma t(v),
$$

$$
\beta | \sigma,v \sim \sigma t(v),
$$

*尤度またはデータモデル*

$$
\mu_i= \alpha + \mathbf{x}_i^T\beta
$$

$$
y_i \sim D(\mu_i,\sigma),
$$

**注意**: $D()$ は `modelClass` に基づく $y_i$ の適切な分布であり、 

  * $$
    \mathbf{E}(y_i)=g(\mu_i)
    $$

    、および
  * $$
    Var(y_i)=\sigma^2
    $$

    。
  * $$
    t(v)
    $$

    は $v$ 自由度の $t$ 分布です。
