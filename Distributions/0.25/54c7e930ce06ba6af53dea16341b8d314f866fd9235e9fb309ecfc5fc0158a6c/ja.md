```
GeneralizedExtremeValue(μ, σ, ξ)
```

*一般化極値分布*は、形状パラメータ`ξ`、スケール`σ`、および位置`μ`を持ち、確率密度関数は次のようになります。

$$
f(x; \xi, \sigma, \mu) = \begin{cases}
        \frac{1}{\sigma} \left[ 1+\left(\frac{x-\mu}{\sigma}\right)\xi\right]^{-1/\xi-1} \exp\left\{-\left[ 1+ \left(\frac{x-\mu}{\sigma}\right)\xi\right]^{-1/\xi} \right\} & \text{for } \xi \neq 0  \\
        \frac{1}{\sigma} \exp\left\{-\frac{x-\mu}{\sigma}\right\} \exp\left\{-\exp\left[-\frac{x-\mu}{\sigma}\right]\right\} & \text{for } \xi = 0 \\
    \end{cases}
$$

次の範囲で

$$
x \in \begin{cases}
        \left[ \mu - \frac{\sigma}{\xi}, + \infty \right) & \text{for } \xi > 0 \\
        \left( - \infty, + \infty \right) & \text{for } \xi = 0 \\
        \left( - \infty, \mu - \frac{\sigma}{\xi} \right] & \text{for } \xi < 0
    \end{cases}
$$

```julia
GeneralizedExtremeValue(μ, σ, ξ)      # 形状ξ、スケールσ、位置μを持つ一般化パレート分布。

params(d)       # パラメータを取得します。すなわち (μ, σ, ξ)
location(d)     # 位置パラメータを取得します。すなわち μ
scale(d)        # スケールパラメータを取得します。すなわち σ
shape(d)        # 形状パラメータを取得します。すなわち ξ（時にはcと呼ばれる）
```

外部リンク

  * [ウィキペディアの一般化極値分布](https://en.wikipedia.org/wiki/Generalized_extreme_value_distribution)
