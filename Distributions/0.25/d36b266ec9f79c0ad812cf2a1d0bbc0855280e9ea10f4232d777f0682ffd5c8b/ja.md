```
Chi(ν)
```

*カイ分布* `ν` 自由度の確率密度関数は

$$
f(x; \nu) = \frac{1}{\Gamma(\nu/2)} 2^{1 - \nu/2} x^{\nu-1} e^{-x^2/2}, \quad x > 0
$$

これは [`Chisq`](@ref) 変量の平方根の分布です。

```julia
Chi(ν)       # ν 自由度のカイ分布

params(d)    # パラメータを取得します。すなわち (ν,)
dof(d)       # 自由度を取得します。すなわち ν
```

外部リンク

  * [カイ分布 - Wikipedia](http://en.wikipedia.org/wiki/Chi_distribution)
