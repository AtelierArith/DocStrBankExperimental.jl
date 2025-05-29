```
struct VelocityExtension{A,B}
```

剛性マトリックスとヒルベルト拡張正則化のキャッシュを保持するラッパー。Allaire et al. 2022 ([link](https://doi.org/10.1016/bs.hna.2020.10.004))を参照。

ヒルベルト拡張正則化法は、内積 $\langle\cdot,\cdot\rangle_H$ を持つヒルベルト空間 $H$ 上の同定問題を解くことを含みます。*次の条件を満たす* $g_\Omega\in H$ *を見つける*： $\langle g_\Omega,w\rangle_H =-J^{\prime}(\Omega)(w\boldsymbol{n})~ \forall w\in H.$

これにより、次の2つの利点が得られます：

1. 自然に形状感度を $\partial\Omega$ から境界領域 $D$ へ拡張します。
2. 追加の正則性を持つ $J(\Omega)$ の降下方向を保証します（すなわち、$L^2(\partial\Omega)$ ではなく $H$）。

# 特性

  * `K::A`: $H$ 上の離散化された内積。
  * `cache::B`: [`project!`](@ref) に使用されるキャッシュされたオブジェクト。
