```
FrankCopula{P}
```

フィールド:

  * θ::Real - パラメータ

コンストラクタ

```
FrankCopula(θ)
```

二変量 [Frank](https://en.wikipedia.org/wiki/Copula_(probability_theory)#Most_important_Archimedean_copulas) コピュラは $\theta \in (-\infty,\infty)$ でパラメータ化されています。これは生成器を持つアルキメデスコピュラです:

$$
\phi(t) = -\frac{\log\left(1+e^{-t}(e^{-\theta-1})\right)}{	heta}
$$

いくつかの特別なケースがあります:

  * θ = -∞ のとき、これは WCopula (下フレシェ-ホフディング境界) です
  * θ = 1 のとき、これは IndependentCopula です
  * θ = ∞ のとき、これは MCopula (上フレシェ-ホフディング境界) です

参考文献:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
