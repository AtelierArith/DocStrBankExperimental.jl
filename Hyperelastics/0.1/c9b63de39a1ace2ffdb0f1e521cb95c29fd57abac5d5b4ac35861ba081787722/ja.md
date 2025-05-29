```julia
Bootstrapped8Chain(; ℒinv)

```

# モデル:

$$
W = W_8(\frac{\sum\lambda}{\sqrt{3N}}-\frac{\lambda_{chain}}{\sqrt{N}})+W_{8}(\frac{\lambda_{chain}}{\sqrt{N}})
$$

ここで:

$$
W_8(x) = \mu N (x \mathcal{L}^{-1}(x) + \log\frac{\mathcal{L}^{-1}(x)}{\sinh\mathcal{L}^{-1}(x)})
$$

および

$$
\lambda_{chain} = \sqrt{\frac{I_1}{3}}
$$

# 引数:

  * `ℒinv=TreloarApproximation()`: 使用される逆ランジュバン近似を設定します。

# パラメータ:

  * `μ`
  * `N`

> Miroshnychenko D, Green WA, Turner DM. Composite and filament models for the mechanical behaviour of elastomeric materials. Journal of the Mechanics and Physics of Solids. 2005 Apr 1;53(4):748-70. Miroshnychenko D, Green WA. Heuristic search for a predictive strain-energy function in nonlinear elasticity. International Journal of Solids and Structures. 2009 Jan 15;46(2):271-86.

