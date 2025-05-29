```
MixedCopula{P}
```

フィールド:

```
- θ::Real - パラメータ
```

コンストラクタ

```
MixedCopula(θ)
```

二変量混合コピュラは、$\alpha \in [0,1]$でパラメータ化されています。これは、ピカンズ依存関数を持つ極値コピュラです:

$$
A(t) = \theta t^2 - \theta t + 1
$$

いくつかの特別なケースがあります:

  * θ = 0 のとき、これはIndependentCopulaです

参考文献:

  * [Tawn1988](@cite) Bivariate extreme value theory: models and estimation. Biometrika, 1988.
