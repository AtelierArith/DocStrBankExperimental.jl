```
Chisq(ν)
```

*カイ二乗分布*（通常はχ²と書かれる）で、`ν` 自由度を持つ確率密度関数は

$$
f(x; \nu) = \frac{x^{\nu/2 - 1} e^{-x/2}}{2^{\nu/2} \Gamma(\nu/2)}, \quad x > 0.
$$

`ν` が整数である場合、それは `ν` 個の独立した標準 [`Normal`](@ref) 変数の二乗和の分布です。

```julia
Chisq(ν)     # ν 自由度のカイ二乗分布

params(d)    # パラメータを取得、すなわち (ν,)
dof(d)       # 自由度を取得、すなわち ν
```

外部リンク

  * [カイ二乗分布 - Wikipedia](http://en.wikipedia.org/wiki/Chi-squared_distribution)
