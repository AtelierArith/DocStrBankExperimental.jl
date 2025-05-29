```julia
boundary_robin!(system, ispec, ibc, α, v)

```

種 ispec の境界 ibc にロビン境界条件を設定します：

$$
\mathrm{flux}_{ispec}\cdot \vec n + \alpha u_{ispec}=v
$$

on $\Gamma_{ibc}$

!!! info
    バージョン 0.14 以降、境界条件は `bcondition` 物理コールバック内で定義することが望ましいです。

