```
GaussianCopula{P}
```

フィールド:

  * θ::Real - パラメータ

コンストラクタ

```
GaussianCopula(θ)
```

二変量 [ガウス](https://en.wikipedia.org/wiki/Copula_(probability_theory)#Gaussian_copula) コピュラ。次のように構成されます:

$$
C(u_1, u_2; \theta) = \Phi_{\theta}(\Phi^{-1}(u_1),\Phi^{-1}(u_2))
$$

ここで、$\Phi_{\theta}$ は相関係数 $\theta \in  [-1, 1]$ を持つ標準二変量正規分布の累積分布関数 (CDF) であり、$\Phi^{-1}$ は標準正規分布の分位関数です。

いくつかの特別なケースがあります:

  * θ = -1 のとき、これは WCopula (下フレシェ-ホエフディング境界) です
  * θ = 0 のとき、これは IndependentCopula です
  * θ = 1 のとき、これは MCopula (上フレシェ-ホエフディング境界) です

参考文献:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
