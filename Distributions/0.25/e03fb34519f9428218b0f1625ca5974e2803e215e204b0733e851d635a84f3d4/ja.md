```
SkewNormal(ξ, ω, α)
```

*スキュー正規分布*は、非ゼロの歪みを許可するように正規分布を一般化した連続確率分布です。位置 `ξ`、スケール `ω`、および形状 `α` が与えられると、確率密度関数は次のようになります。

$$
f(x; \xi, \omega, \alpha) =
\frac{2}{\omega \sqrt{2 \pi}} \exp{\bigg(-\frac{(x-\xi)^2}{2\omega^2}\bigg)}
\int_{-\infty}^{\alpha\left(\frac{x-\xi}{\omega}\right)}
\frac{1}{\sqrt{2 \pi}}  \exp{\bigg(-\frac{t^2}{2}\bigg)} \, \mathrm{d}t
$$

外部リンク

  * [スキュー正規分布 - Wikipedia](https://en.wikipedia.org/wiki/Skew_normal_distribution)
  * [Discourse](https://discourse.julialang.org/t/skew-normal-distribution/21549/7)
  * [SkewDist.jl](https://github.com/STOR-i/SkewDist.jl)
