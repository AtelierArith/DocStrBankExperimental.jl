```
AMHCopula{P}
```

フィールド:

  * θ::Real - パラメータ

コンストラクタ

```
AMHCopula(θ)
```

二変量 [AMH](https://en.wikipedia.org/wiki/Copula_(probability_theory)#Most_important_Archimedean_copulas) コピュラは $\theta \in [-1,1)$ でパラメータ化されています。これは生成器を持つアルキメデスコピュラです:

$$
\phi(t) = 1 - \frac{1-\theta}{e^{-t}-\theta}
$$

いくつかの特別なケースがあります:

  * θ = 0 のとき、これは IndependentCopula です
  * θ = 1 のとき、これは UtilCopula です

参考文献:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
