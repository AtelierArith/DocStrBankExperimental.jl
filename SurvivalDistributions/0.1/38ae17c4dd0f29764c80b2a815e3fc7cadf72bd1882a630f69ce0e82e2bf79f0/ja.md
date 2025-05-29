```
ExponentiatedWeibull(α,θ,γ)
```

[Exponentiated Weibull distribution](https://en.wikipedia.org/wiki/Exponentiated_Weibull_distribution)は、[Weibull distribution](https://en.wikipedia.org/wiki/Weibull_distribution)の累積分布関数を指数化することによって得られます。この単純な変換は、興味深いことに、ハザード関数に多くの柔軟性をもたらす第二の形状パラメータを追加します。Exponentiated Weibull distributionのハザード関数は、定常、増加、減少、バスタブ、単峰などの基本的な形状を捉えることができ、サバイバルモデルにとって魅力的です。

ランダム変数Xは、累積分布関数が$F_X = F_W^{γ}$であるとき、`ExponentiatedWeibull(α,θ,γ)`分布に従います。ここで、$F_W$は`Weibull(α,θ)`の累積分布関数です。

参考文献:

  * [Exponentiated Weibull distribution](https://en.wikipedia.org/wiki/Exponentiated_Weibull_distribution)
  * [Weibull distribution](https://en.wikipedia.org/wiki/Weibull_distribution)
