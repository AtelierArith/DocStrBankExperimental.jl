```
tCopula{P}
```

フィールド:     - ν::Real - パラメータ     - θ::Real - パラメータ 

コンストラクタ

```
tCopula(ν, θ)
```

二変量tコピュラ。次のように構築されます: 

$$
C(u_1, u_2; \nu, \theta) = t_{\nu, \theta}(t_{\nu}^{-1}(u_1),t_{\nu}^{-1}(u_2))
$$

ここで、$t_{\nu, \theta}$は、$\nu \in \mathbb{R}^{+}$ 自由度、ゼロ平均、相関 $\theta \in [-1, 1]$ の二変量t分布の累積分布関数 (CDF) であり、$t_{\nu}^{-1}$ は、$\nu$ 自由度の標準t分布の分位関数です。

いくつかの特別なケースがあります:

  * θ = -1 のとき、これはWCopula（下フレシェ-ホエフディング境界）です
  * θ = 0 のとき、これはIndependentCopulaです
  * θ = 1 のとき、これはMCopula（上フレシェ-ホエフディング境界）です

参考文献:

  * [joe2014](@cite) Joe, Harry. Dependence modeling with Copulas. Chapman & Hall, 2014.
