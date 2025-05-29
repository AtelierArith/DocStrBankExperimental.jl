```
MaxwellBoltzmann(scale::Real)
```

*マクスウェル・ボルツマン分布*のスケールパラメータ`a`を持つ確率密度関数は次のようになります。

$$
f(x,a) = \sqrt{\frac{2}{\pi}}\frac{x^2}{a^3}\exp\left(\frac{-x^2}{2a^2}\right)
$$

マクスウェル・ボルツマン分布は、性質$X\sim \operatorname{MaxwellBoltzmann}(a=1)$を通じて`Chi`分布に関連しており、その場合$X\sim\chi(\mathrm{dof}=3)$となります。

外部リンク

  * [マクスウェル・ボルツマン分布 - Wikipedia](https://en.wikipedia.org/wiki/Maxwell–Boltzmann_distribution)
  * [マクスウェル・ボルツマン分布 - Wolfram MathWorld](https://mathworld.wolfram.com/MaxwellDistribution.html)
  * [Scipyにおけるマクスウェル・ボルツマン分布の実装](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.maxwell.html)
