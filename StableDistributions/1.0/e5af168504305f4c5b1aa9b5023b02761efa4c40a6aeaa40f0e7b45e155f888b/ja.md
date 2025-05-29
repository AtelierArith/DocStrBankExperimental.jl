```
Stable(α, β, σ, μ)
```

*安定分布*は、安定性指数 0 < `α` ≤ 2、歪度パラメータ -1 ≤ `β` ≤ 1、スケール 0 < `σ` および位置 `μ` を持ち、特性関数は次のようになります。

$$
\varphi(t; \alpha, \beta, \sigma, \mu) = \exp\big(\mathrm i t\mu -|\sigma t|^\alpha(1-\mathrm i\beta\mathrm{sgn}(t)\Phi(t))\big)
$$

ここで、α = 1 の場合は $\Phi(t) = -\frac{2}{\pi}\log|t|$、α ≠ 1 の場合は $\Phi(t) = \tan(\pi\alpha/2)$ です。タイプ1のパラメータ化を使用します。

```julia
Stable(α)             # 標準対称α-安定分布はStable(α, 0, 1, 0)に相当
Stable(α, β)          # 歪度パラメータβを持つ標準α-安定分布はS(α, β, 1, 0)に相当
Stable(α, β, σ, μ)    # 歪度パラメータβ、スケールσ、位置μを持つα-安定分布

params(d)             # パラメータを取得、すなわち (α, β, σ, μ)
shape(d)              # 形状を取得、すなわち (α, β)
location(d)           # 位置を取得、すなわち μ
scale(d)              # スケールを取得、すなわち σ
minimum(d)            # 下限を取得
maximum(d)            # 上限を取得
```

外部リンク

  * [Stable distribution on Wikipedia](https://en.wikipedia.org/wiki/Stable_distribution)
