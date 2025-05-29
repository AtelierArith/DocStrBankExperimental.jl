```
 SHO(A, ω₀, Q)
```

単純調和振動子の共分散関数

  * `A`: 共分散関数の振幅
  * `ω₀`: 単純調和振動子の角周波数
  * `Q`: 単純調和振動子の品質係数

$$
k(τ) = A \exp(-ω₀ τ / Q / 2) \left\{\begin{matrix} 2(1 + ω₀ τ) & Q = 1/2 \\ \cos(η ω₀ τ) + \frac{\sin(η ω₀ τ)}{2η Q} & Q < 1/2 \\ \cosh(η ω₀ τ) + \frac{\sinh(η ω₀ τ)}{2η Q} & Q \geq 1/2 \end{matrix}\right.\\
η = \sqrt{\left|1 - \frac{1}{4 Q^2}\right|}
$$

詳細については[Foreman-Mackey et al. (2017)](https://ui.adsabs.harvard.edu/abs/2017AJ....154..220F)を参照してください。
