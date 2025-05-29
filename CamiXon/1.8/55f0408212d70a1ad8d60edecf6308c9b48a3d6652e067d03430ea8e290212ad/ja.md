```
UG(spinorbit1::Spinorbit, spinorbit2::Spinorbit, P1::Vector{T}, P2::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

2つの電子の*交換*スクリーニングのポテンシャルで、(縮小された) 波動関数 `P1` と `P2` に対応し、電子軌道 `orbit1` と `orbit2` に対応します。

注: `UG(spinorbit1, spinorbit2, P1, P2, grid)` = `UG(spinorbit2, spinorbit1, P1, P2, grid)`

$$
U_{G}(u_{\kappa},u_{\kappa^{\prime}};\rho)
={\textstyle \sum\limits_{k=0}^{\infty}}b^{k}(lm_{l};l^{\prime}m_{l^{\prime}})U_{G}^{k}(nl,n^{\prime}l^{\prime};\rho).
$$

#### 例:

```

```
