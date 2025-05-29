```
UF(spinorbit1::Spinorbit, spinorbit2::Spinorbit, P2::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

スピン軌道 `orbit 1` における観測者電子に対する*直接的*スクリーン効果のポテンシャルは、スクリーン電子 `orbit2` によって与えられ、（縮小された）放射状波動関数 `P2` を用います。

$$
U_{F}(u_{\kappa},u_{\kappa^{\prime}};\rho)
={\textstyle \sum\limits_{k=0}^{\infty}}a^{k}(lm_{l};l^{\prime}m_{l^{\prime}})U_{F}^{k}(nl;\rho).
$$

#### 例:

```

```
