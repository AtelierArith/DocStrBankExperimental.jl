```
SkewedExponentialPower(μ, σ, p, α)
```

*歪んだ指数冪分布*は、位置 `μ`、スケール `σ`、形状 `p`、および歪度 `α` を持ち、確率密度関数は次のようになります[1]

$$
f(x; \mu, \sigma, p, \alpha) =
\begin{cases}
\frac{1}{\sigma 2p^{1/p}\Gamma(1+1/p)} \exp \left\{ - \frac{1}{2p}\Big| \frac{x-\mu}{\alpha \sigma} \Big|^p \right\}, & \text{if } x \leq \mu \\
\frac{1}{\sigma 2p^{1/p}\Gamma(1+1/p)} \exp \left\{ - \frac{1}{2p}\Big| \frac{x-\mu}{(1-\alpha) \sigma} \Big|^p \right\}, & \text{if } x > \mu
\end{cases}.
$$

歪んだ指数冪分布（SEPD）は、ラプラス（$p=1, \alpha=0.5$）、正規（$p=2, \alpha=0.5$）、一様（$p\rightarrow \infty, \alpha=0.5$）、非対称ラプラス（$p=1$）、歪んだ正規（$p=2$）、および指数冪分布（$\alpha = 0.5$）を特別なケースとして含んでいます。

[1] Zhy, D. and V. Zinde-Walsh (2009). Properties and estimation of asymmetric exponential power distribution. *Journal of econometrics*, 148(1):86-96, 2009.

```julia
SkewedExponentialPower()            # SEPDは形状2、スケール1、位置0、歪度0.5（標準正規分布）
SkewedExponentialPower(μ, σ, p, α)  # SEPDは位置μ、スケールσ、形状p、歪度α
SkewedExponentialPower(μ, σ, p)     # SEPDは位置μ、スケールσ、形状p、歪度0.5（指数冪分布）
SkewedExponentialPower(μ, σ)        # SEPDは位置μ、スケールσ、形状2、歪度0.5（正規分布）
SkewedExponentialPower(μ)           # SEPDは位置μ、スケール1、形状2、歪度0.5（正規分布）

params(d)       # パラメータを取得、すなわち (μ, σ, p, α)
shape(d)        # 形状パラメータを取得、すなわち p
location(d)     # 位置パラメータを取得、すなわち μ
scale(d)        # スケールパラメータを取得、すなわち σ
```
