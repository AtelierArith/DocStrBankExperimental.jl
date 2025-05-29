```
HuslerReissCopula{P}
```

フィールド:

```
- θ::Real - パラメータ
```

コンストラクタ

```
HuslerReissCopula(θ)
```

二変量Husler-Reissコピュラは、$\theta \in [0,\infty)$でパラメータ化されています。これは、ピカンズ依存関数を持つ極値コピュラです:

$$
A(t) = t\Phi(\theta^{-1}+\frac{1}{2}\theta\log(\frac{t}{1-t})) +(1-t)\Phi(\theta^{-1}+\frac{1}{2}\theta\log(\frac{1-t}{t}))
$$

ここで、$\Phi$は標準正規分布の累積分布関数（CDF）です。

いくつかの特別なケースがあります:

  * θ = 0 のとき、これは独立コピュラです
  * θ = ∞ のとき、これはMコピュラ（上フレシェ-ホエフディング境界）です

参考文献:

  * [Husler1989](@cite) Maxima of normal random vectors: between independence and complete dependence. Statist. Probab. 1989.
