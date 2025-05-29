```
HorvitzThompson <: DiscreteInfoEstimatorShannon
HorvitzThompson(measure::Shannon = Shannon())
```

`HorvitzThompson`推定量は、[`information`](@ref)と共に使用され、[Horvitz1952](@citet)に従って離散[`Shannon`](@ref)エントロピーを計算します。

# 説明

[`Shannon`](@ref)エントロピーのホーヴィッツ・トンプソン推定量は次のように与えられます。

$$
H_S^{HT} = -\sum_{i=1}^M \dfrac{p_i \log(p_i) }{1 - (1 - p_i)^N},
$$

ここで、$N$はサンプルサイズ、$M$は[`outcomes`](@ref)の数です。$i$-番目の結果の真の確率$p_i$が与えられたとき、$1 - (1 - p_i)^N$は、サイズ$N$のサンプルでその結果が少なくとも1回現れる確率です[Arora2022](@cite)。この包含確率で割ることは重み付けの一形態であり、特定の結果が非常に低い確率を持っているためにサンプルであまり観察されない状況を補償します。例えば、パワー法則分布においてです。
