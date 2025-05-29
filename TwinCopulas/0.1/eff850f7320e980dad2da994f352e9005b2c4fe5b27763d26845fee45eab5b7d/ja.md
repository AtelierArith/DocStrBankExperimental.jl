```
Nelsen2Copula{P}
```

フィールド:

  * θ::Real - パラメータ

コンストラクタ

```
Nelsen2Copula(θ)
```

二変量Nelsen2Copulaコピュラは、$\theta \in [1,\infty)$でパラメータ化されています。これは、生成器を持つアルキメデスコピュラです：

$$
\phi(t) = 1 - t^{\frac{1}{\theta}}
$$

いくつかの特別なケースがあります：

  * θ = 1 のとき、これはIndependentCopulaです
  * θ = ∞ のとき、これはMCopula（上フレシェ-ホエフディング境界）です

参考文献:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
