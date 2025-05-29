```
PowerGeneralizedWeibull(σ,ν,γ)
```

パワー一般化ワイブル（PGW）分布は、${\mathbb R}_+$上でサポートされる三パラメータ分布です。対応するハザード関数は、バスタブ型、単峰型、および単調（増加および減少）ハザード形状を受け入れることができます。PGW分布は、そのハザードおよび生存関数の扱いやすさから、生存分析において人気があります。

`PowerGeneralizedWeibull(σ,ν,γ)`分布は、スケール`σ`、形状`ν`（ニュー）、および第二形状`γ`を持ち、確率密度関数は次のようになります。

$$
f(t;σ,ν,γ) = \dfrac{ν}{γ σ^ν}t^{ν-1} \left[ 1 + \left(\dfrac{t}{σ}\right)^ν\right]^{\left(\frac{1}{γ}-1\right)} \exp\left\{ 1- \left[ 1 + \left(\dfrac{t}{σ}\right)^ν\right]^{\frac{1}{γ}}
\right\}.
$$

参考文献:

  * [nikulin:2009](@cite) Nikulin, M. and Haghighi, F. On the power generalized Weibull family: model for cancer censored data. Metron – International Journal of Statistics, 2009
