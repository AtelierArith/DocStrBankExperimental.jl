```julia
breaction!(
    f,
    u,
    bnode,
    data,
    _::Type{ChargeTransport.OhmicContactDirichlet}
)

```

ディリクレ境界条件を介してオーム境界条件を作成します。静電ポテンシャル $\psi$

$$
\psi  = \psi_0 + U
$$

,

ここで、$\psi_0$ は与えられた値を含み、$U$ は適用された電圧です。

$$
f[\psi] =  -q/\delta  \sum_\alpha{ z_\alpha  (n_\alpha - C_\alpha) },
$$

ここで、$C_\alpha$ は種 $\alpha$ に対するいくつかのドーピングに対応します。

電子とホールの境界条件はディリクレ条件であり、

$$
\varphi_{\alpha} = U.
$$

`
