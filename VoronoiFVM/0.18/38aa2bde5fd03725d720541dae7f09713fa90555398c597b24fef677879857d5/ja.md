```julia
boundary_dirichlet!(system, ispec, ibc, v)

```

種 ispec の Dirichlet 境界条件を境界 ibc に設定します：

$$
u_{ispec}=v
$$

on $\Gamma_{ibc}$

!!! info
    バージョン 0.14 以降、`bcondition` 物理コールバック内で境界条件を定義することが望ましいです。

