```
TDist(ν)
```

*スチューデントのT分布*は、`ν` 自由度を持ち、確率密度関数は次のようになります。

$$
f(x; \nu) = \frac{1}{\sqrt{\nu} B(1/2, \nu/2)}
\left( 1 + \frac{x^2}{\nu} \right)^{-\frac{\nu + 1}{2}}
$$

```julia
TDist(d)      # ν 自由度のt分布

params(d)     # パラメータを取得します。すなわち (ν,)
dof(d)        # 自由度を取得します。すなわち ν
```

外部リンク

[ウィキペディアのスチューデントのT分布](https://en.wikipedia.org/wiki/Student%27s_t-distribution)
