```
AsymMixedCopula{P}
```

フィールド:

  * θ::Vector - パラメータ (サイズ 2)

コンストラクタ

```
AsymMixedCopula(θ)
```

非対称二変量混合コピュラは、次の条件を満たす必要がある2つのパラメータ $\theta_{i}, i=1,2$ によってパラメータ化されています:

  * θ₁ ≥ 0
  * θ₁+θ₂ ≤ 1
  * θ₁+2θ₂ ≤ 1
  * θ₁+3θ₂ ≥ 0

これは、ピカンズ依存関数を持つ極値コピュラです:

$$
A(t) = \theta_{2}t^3 + \theta_{1}t^2-(\theta_1+\theta_2)t+1
$$

いくつかの特別なケースがあります:

  * θ₁ = θ₂ = 0 の場合、これは独立コピュラです
  * θ₂ = 0 の場合、これは混合コピュラです

参考文献:

  * [Tawn1988](@cite) Bivariate extreme value theory: models and estimation. Biometrika, 1988.
