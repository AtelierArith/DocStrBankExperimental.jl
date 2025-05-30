```
FDist(ν1, ν2)
```

*F分布*の確率密度関数は次のようになります。

$$
f(x; \nu_1, \nu_2) = \frac{1}{x B(\nu_1/2, \nu_2/2)}
\sqrt{\frac{(\nu_1 x)^{\nu_1} \cdot \nu_2^{\nu_2}}{(\nu_1 x + \nu_2)^{\nu_1 + \nu_2}}}, \quad x>0
$$

これは、$X_1 \sim \operatorname{Chisq}(\nu_1)$および$X_2 \sim \operatorname{Chisq}(\nu_2)$であるとき、$(X_1/\nu_1) / (X_2 / \nu_2) \sim \operatorname{FDist}(\nu_1, \nu_2)$という性質を通じて[`Chisq`](@ref)分布に関連しています。

```julia
FDist(ν1, ν2)     # パラメータν1およびν2を持つF分布

params(d)         # パラメータを取得します。すなわち(ν1, ν2)
```

外部リンク

  * [F分布 - Wikipedia](http://en.wikipedia.org/wiki/F-distribution)
